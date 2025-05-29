```
mutable struct SubresultantAlgorithm <: AbstractUnivariateGCDAlgorithm
    skipped_divisions::Int
end
```

サブリザルタントアルゴリズムを使用して一変数多項式の最大公約数を計算するアルゴリズム、詳細は[Knu14, Algorithm C, p. 428-429]を参照してください。

アルゴリズムにおける`g*h^δ`による除算は、除算される多項式にゼロ項がある場合でも[Knu14, Algorithm R, p. 426]の反復が実行される場合にのみ機能します。計算の節約のために、私たちはそれを行わないので、`skipped_division`にスキップされた除算の数を保存し、`g*h^δ`による除算をそれに応じて調整できるようにします。

[Knu14, Algorithm C, p. 426]では、次のように述べられています。``

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
