```
fit(D, args...)
```

タイプ `D` の分布を `args` にフィットさせます。

fit 関数は、分布をフィットさせるための合理的な方法を選択します。ほとんどの場合、これは最尤推定です。このアルゴリズムは変更される可能性があることに注意してください。一貫して動作する関数については、`fit_mle` を参照してください。

デフォルトでは、フォールバックは [`fit_mle(D, args...)`](@ref) です。開発者は、特定の分布タイプ `D <: Distribution` に対して `fit(::Type{D}, args...)` メソッドを定義することで、このデフォルトを変更できます。
