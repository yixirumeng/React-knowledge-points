## React知识点

[1、为什么不能直接修改组件状态](#为什么不能直接修改组件状态)

[2、children属性](#children属性)

1. ### 为什么不能直接修改组件状态

    如果直接修改组件的`state`，即`this.state.title = 'hello'`，则不会触发组件重新渲染。想要让组件重新渲染，则需要执行组件的`render`方法，而`react`提供的`setState`方法可以使得组件重新执行一遍`render`方法，所以想要修改`state`则想要使用`setState`方法。

2. ### children属性

    Children是一个属性，可以将组件作为数据传递给其他组件。简单来说，通过`this.props.chldren`，可以获取到在组件的开始和结束标记之间放置的组件树。

    `this.props.chldren`的值有三种可能性：
    
        如果没有子节点，其值为undefined；如果有一个子节点，其值为object；如果有多个子节点，其值为array

    同时提供了很多方法：

    1. **`React.Children.map(object children, function fn [, object context])`**（`fn`中的`this`指向上下文，也可以使用第三个参数设置绑定的上下文），其返回值为`object`类型的对象

        如果`children`是一个对象或数组，将被遍历，每个元素调用`fn`方法；如果`children`是`null`或者`undefined`，则直接返回，而不是返回空对象

    2. **`React.Children.forEach(object children, function fn [, object context])`** 类似`map`方法，但是不返回对象

    3. **`React.Children.count(object children)`** 返回`children`内的组件数

    4. **`React.Children.only(object children)`** 返回`children`中 仅有的子级。否则抛出异常。

        其接受的参数只能是一个对象，不能是多个对象或数组，如：

        ```
        console.log(React.Children.only(this.props.children[0]));
        //输出对象this.props.children[0]
        ```
    5. **`React.Children.toArray`** 将`children`对象转换为数组
