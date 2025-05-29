```
check_method(func, signature, acceptable_instability=Dict())
```

`StabilityReport`オブジェクトを作成し、メソッドの型の安定性を説明します。

変数と戻り値の非具体的な型を計算し、それらを[`StabilityReport`](@ref)オブジェクトに返します。

`acceptable_instability`が存在する場合、それは非具体的な型が許可される変数のマッピングです。`get`はマッピング、変数のシンボル、および`Bool`を使用して変数の許可された型を取得するために呼び出されます。さらに、戻り値はシンボルとして`:return`を使用してチェックされます。
