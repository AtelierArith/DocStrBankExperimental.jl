```
ScatteringProcess <: AbstractProcessDefinition
```

任意の粒子の散乱過程の一般的な実装。現在、`PerturbativeQED`との組み合わせでの計算のみがサポートされています。しかし、これは任意の数の入射粒子と出射粒子、及び粒子のスピンや偏光の任意の組み合わせを持つ散乱過程を記述することを目的としています。

[`isphysical`](@ref) 関数を使用して、過程が摂動QEDで可能かどうかを確認できます。

!!! warning
    現在、断面積と確率の計算は未実装です。


## コンストラクタ

```
ScatteringProcess(
    in_particles::Tuple{AbstractParticleType},
    out_particles::Tuple{AbstractParticleType},
    [in_sp::Tuple{AbstractSpinOrPolarization},
    out_sp::Tuple{AbstractSpinOrPolarization}]
)
```

指定された入射粒子と出射粒子、およびそれぞれのスピンと偏光を持つScatteringProcessのコンストラクタ。コンストラクタは、粒子がそれぞれのスピンと偏光と互換性があることを確認します。アサーションが失敗した場合、`InvalidInputError`がスローされます。

`in_sp`および`out_sp`パラメータは省略可能で、その場合、すべてのフェルミオンとボソンに対して、すべてのスピンと偏光が`AllSpin`および`AllPol`に設定されます。
