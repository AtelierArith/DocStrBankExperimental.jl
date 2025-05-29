```
pyproperty(; get=nothing, set=nothing, del=nothing, doc=nothing)
pyproperty(get)
```

指定されたゲッター、セッター、およびデリータを持つPythonの`property`を作成します。

`get`、`set`、または`del`がPythonオブジェクトでない場合（例えば、`Function`の場合）、それは[`pyfunc`](@ref PythonCall.pyfunc)を使用してPythonオブジェクトに変換されます。特に、これにより渡される引数は常に`Py`型になります。
