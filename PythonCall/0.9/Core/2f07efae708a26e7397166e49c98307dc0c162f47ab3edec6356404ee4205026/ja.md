```
pyeval([T=Py], code, globals, locals=nothing)
```

与えられたPython `code`を評価し、結果を`T`として返します。

`globals`が`Module`の場合、そのモジュールに固有の永続的な`dict`が使用されます。

デフォルトでは、コードはグローバルスコープで実行されます（すなわち、`locals===globals`）。一時的なローカルスコープを使用するには、`locals`を`()`に設定するか、スコープに含める変数の`NamedTuple`に設定します。

詳細は[`@pyeval`](@ref)を参照してください。

# 例

以下は、`Main`モジュールで`1.1+2.2`を`Float64`として計算します：

```
pyeval(Float64, "x+y", Main, (x=1.1, y=2.2))  # returns 3.3
```
