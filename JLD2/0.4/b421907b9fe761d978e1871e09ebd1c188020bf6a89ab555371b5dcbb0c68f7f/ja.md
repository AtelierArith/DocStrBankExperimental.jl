```
@load filename var1 [var2 ...]
```

JLD2ファイル`filename`から1つ以上の変数`var1,...`を現在のスコープにロードし、ロードされた変数名のベクトルを返します。

対話的な使用のために、`@load "somefile.jld2"`の形式は、`"somefile.jld2"`からすべての変数を現在のスコープにロードします。この形式はリテラルファイル名のみをサポートし、変数の出所が明確になるように、より永続的なコードでは避けるべきです。

# 例

ファイルexample.jld2から変数`hello`と`foo`をロードするには、次のようにします。

```julia
@load "example.jld2" hello foo
```
