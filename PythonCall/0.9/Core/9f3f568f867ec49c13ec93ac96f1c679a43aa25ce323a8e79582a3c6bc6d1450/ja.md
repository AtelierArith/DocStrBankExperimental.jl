```
pytype(name, bases, dict)
```

新しい型を作成します。Pythonの`type(name, bases, dict)`に相当します。

`bases`がPythonオブジェクトでない場合、`pytuple`を使用してPythonオブジェクトに変換されます。

`dict`はPythonオブジェクトまたはJuliaのイテラブルである場合があります。後者の場合、各アイテムは`name => value`ペアまたは`__name__`属性を持つPythonオブジェクトである可能性があります。

Juliaの`Function`をインスタンスメソッドとして使用するには、[`pyfunc`](@ref PythonCall.pyfunc)を使用してPython関数にラップする必要があります。同様に、[`pyclassmethod`](@ref PythonCall.pyclassmethod)、[`pystaticmethod`](@ref PythonCall.pystaticmethod)または[`pyproperty`](@ref PythonCall.pyproperty)も参照してください。これらすべての場合、関数に渡される引数は常に`Py`型です。以下の例を参照してください。

# 例

```julia
Foo = pytype("Foo", (), [
    "__module__" => "__main__",

    pyfunc(
        name = "__init__",
        doc = """
        Fooに格納するxとyを指定します。

        省略した場合、yはNoneにデフォルト設定されます。
        """,
        function (self, x, y = nothing)
            self.x = x
            self.y = y
            return
        end,
    ),

    pyfunc(
        name = "__repr__",
        self -> "Foo($(self.x), $(self.y))",
    ),

    pyclassmethod(
        name = "frompair",
        doc = "長さ2のタプルからFooを構築します。",
        (cls, xy) -> cls(xy...),
    ),

    pystaticmethod(
        name = "hello",
        doc = "フレンドリーな挨拶を印刷します。",
        (name) -> println("Hello, $name"),
    ),

    "xy" => pyproperty(
        doc = "xとyのタプル。",
        get = (self) -> (self.x, self.y),
        set = function (self, xy)
            (x, y) = xy
            self.x = x
            self.y = y
            nothing
        end,
    ),
])
```
