[`Abbreviation`](@ref)は、現在のモジュール内で文書化された`Method`、`Function`、または`DataType`に一致するすべてのメソッドのリストを含めるためのものです。

# 例

生成されたマークダウンテキストは、関数`f`が異なる2つのメソッド（1つは数値を受け取り、もう1つは文字列を受け取る）を定義する以下の例に似たものになります。

````markdown
```julia
f(num)
```

[`<path>:<line>`](<github-url>)で定義されています。

```julia
f(str)
```

[`<path>:<line>`](<github-url>)で定義されています。
````
