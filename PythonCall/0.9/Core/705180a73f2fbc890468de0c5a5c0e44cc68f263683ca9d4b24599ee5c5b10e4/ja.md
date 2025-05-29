```
pyexec([T=Nothing], code, globals, locals=nothing)
```

与えられたPython `code`を実行します。

`globals`が`Module`の場合、そのモジュールに固有の永続的な`dict`が使用されます。

デフォルトでは、コードはグローバルスコープで実行されます（すなわち`locals===globals`）。一時的なローカルスコープを使用するには、`locals`を`()`に設定するか、スコープに含める変数の`NamedTuple`に設定します。

`T==Nothing`の場合は`nothing`を返します。それ以外の場合、`T`は具体的な`NamedTuple`型でなければならず、`locals`から対応するアイテムが抽出されて返されます。

詳細は[`@pyexec`](@ref)を参照してください。

# 例

以下は、`Main`モジュールで`1.1+2.2`を`Float64`として計算します：

```
pyexec(@NamedTuple{ans::Float64}, "ans=x+y", Main, (x=1.1, y=2.2))  # returns (ans = 3.3,)
```

変数を`global`としてマークすると、それらはモジュールスコープに保存され、以降の呼び出しで利用可能になります：

```
pyexec("global x; x=12", Main)
pyeval(Int, "x", Main)  # returns 12
```
