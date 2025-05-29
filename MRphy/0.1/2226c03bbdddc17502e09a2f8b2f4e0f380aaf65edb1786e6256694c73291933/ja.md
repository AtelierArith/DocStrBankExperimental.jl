```
blochSim!(M, A, B)
```

Hargreaveの𝐴/𝐵、mat/vecに基づくブロッホシミュレーション。スピンに対して行列`A`とベクトル`B`をグローバルまたはスピン単位で適用します。スピン`M`はdoi:10.1002/mrm.1170で説明されています。

*入力*:

  * `M::TypeND(Real, [2])` (nM, xyz): 入力スピンの磁化。
  * `A::TypeND(AbstractFloat,[3])` (nM, 3,3), `A[iM,:,:]`は`iM`-th 𝐴です。
  * `B::TypeND(AbstractFloat,[2])` (nM, 3), `B[iM,:]`は`iM`-th 𝐵です。

*出力*:

  * `M::TypeND(Real, [2])` (nM, xyz): `B`を適用した後のスピン。
