```
TableTransform
```

テーブルを入力として受け取り、新しいテーブルを生成する変換です。`TableTransform`トレイトを実装する任意の変換は、[`apply`](@ref)関数を実装する必要があります。変換が[`isrevertible`](@ref)である場合、[`revert`](@ref)関数も実装する必要があります。

上記の関数から自動的にファンクタインターフェースが生成されるため、`TableTransform`トレイトを実装する任意の変換は、[Tables.jl](https://github.com/JuliaData/Tables.jl)インターフェースを実装する任意のテーブルで直接評価できます。
