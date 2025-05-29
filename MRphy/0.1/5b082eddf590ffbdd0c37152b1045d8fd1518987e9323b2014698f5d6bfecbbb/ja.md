```
B2AB(B; T1=(Inf)u"s", T2=(Inf)u"s", γ=γ¹H, dt=(4e-6)u"s")
```

Hargreaveの𝐴/𝐵にB効果的を変換し、mat/vec、参照: doi:10.1002/mrm.1170。

*入力*:

  * `B::Union{TypeND(B0D, [2,3]), Base.Generator}`: グローバル、(nT,xyz); スピンごと、(nM,xyz,nT)。

*キーワード*:

  * `T1 & T2 ::TypeND(T0D, [0,1])`: グローバル、(1,); スピンごと、(nM,1)。
  * `γ::TypeND(Γ0D, [0,1])`: グローバル、(1,); スピンごと、(nM, 1)。ジャイロ比
  * `dt::T0D` (1,), シミュレーションの時間ステップサイズ、すなわち、滞留時間。

*出力*:

  * `A::TypeND(AbstractFloat,[3])` (nM, 3,3)、`A[iM,:,:]`は`iM`-th 𝐴です。
  * `B::TypeND(AbstractFloat,[2])` (nM, 3)、`B[iM,:]`は`iM`-th 𝐵です。

参照: [`rfgr2B`](@ref)、[`Pulse2B`](@ref)。
