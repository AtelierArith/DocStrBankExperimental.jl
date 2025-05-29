```
sum_mutating!(accumulator, [f! = add!], keys(::PDVec); [init])
sum_mutating!(accumulator, [f! = add!], values(::PDVec); [init])
sum_mutating!(accumulator, [f! = add!], pairs(::PDVec); [init])
```

ベクトル値の結果のために[`PDVec`](@ref)sで並列合計を実行し、アロケーションを最小限に抑えます。合計の結果は`accumulator`に追加され、`accumulator`に格納されます。MPI互換です。`f!`が提供されている場合、それは2つの引数を受け入れる必要があります。最初の引数はアキュムレーターで、2番目の引数はイテレーターの要素です。そうでない場合は、`add!`が使用されます。

提供されている場合、`init`は`+`の中立要素であり、`accumulator`と同じ型でなければなりません。

[`mapreduce`](@ref)も参照してください。
