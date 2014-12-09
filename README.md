TouchDemo
=========
	/*** 事件拦截机制：
	 * onInterceptTouchEvent 负责事件的拦截
	 * dispatchToucheEvent   负责事件的派发
	 * onTouchEvent          负责事件的处理
	 * 
	 *假如layout 关系 父---->子  如下：
	 *  一、
	 *  
	 * A---->B------>C----->AT
	 * 
	 * A B C的onInterceptTouchEvent 都返回false，不进行拦截  并且A B C AT 的onTouchEvent 都返回false
	 * 
	 * 
	 * A:onInterceptTouchEvent ------>B:onInterceptTouchEvent---->C:onInterceptTouchEvent--->AT:onToucheEvent--->
	 * C:onTouchEvent----->B:onTouchEvent---->A:onTouchEvent
	 * 
	 * 整个事件的流程传递 类似一个U字母   ： onInterceptTouchEvent 方法 是由父传递到子， onToucheEvent 方法是由子传递到父
	 * 
	 * 
	 * 二、
	 * 
	 * 如果C的onInterceptTouchEvent返回false  既是C把事件拦截下来，那么 事件不再往下传递，而是传递给C的onTouchEvent事件，
	 * 如果C：onTouchEvent返回true,则C处理，如果返回false，则往父类传递
	 * 
	 * 三、
	 * 如果都返回false：
	 * onInterceptTouchEvent 事件顺序 ： Activity 传递给 viewGroup 再传递给view,
	 * 然后onTouchEvent事件 有view  viewGroup Activity顺序传递，最后有Acitivity接受并处理
	 * 
	 *  Android中的控件有两种： View是基类
	 *  1、继续View不能包含其他控件的控件
	 *  2、继承ViewGroup可以包含其它控件的控件：成为容器控件：如listview GridView LinearLayout
	 *     ViewGroup继承View,ViewGroup中多了一个onInterceptTouchEvent进行事件的拦截
	 * 
	 */
