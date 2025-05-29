!!! warning
    この種の機能でユーザーが自分自身を傷つけるのを防ぐのは比較的難しいです。これに注意してください。セグメンテーションフォルトは慎重に予想されるべきです。


```julia
lambda(m::Module, src::Core.CodeInfo)
lambda(m::Module, src::Core.CodeInfo, nargs::Int)
const λ = lambda
```

`src::Core.CodeInfo`の一部から匿名の`@generated`関数を作成します。`src::Core.CodeInfo`は[`verify`](@ref)によって整合性がチェックされます。

`lambda`には2つの異なる形式があります。最初の形式は、次のシグネチャによって与えられます：

```julia
lambda(m::Module, src::Core.CodeInfo)
```

これは自動的に正しい引数の数を検出しようとします。これは（内部的な理由で）失敗する可能性があります。これを考慮して、2番目の形式は次のシグネチャによって与えられます：

```julia
lambda(m::Module, src::Core.CodeInfo, nargs::Int)
```

これにより、ユーザーは`nargs`を介して引数の数を指定できます。

`lambda`には、Unicodeを愛する人々のための省略形`λ`もあります。
