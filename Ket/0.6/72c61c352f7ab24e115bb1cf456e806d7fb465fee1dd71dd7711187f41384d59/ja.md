```
schmidt_number(
    ρ::AbstractMatrix{T},
    s::Integer = 2,
    dims::AbstractVecOrTuple = _equal_sizes(ρ),
    n::Integer = 1;
    ppt::Bool = true,
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

シュミット数 `s` を持つような `ρ` のホワイトノイズロバスト性の上限。

もし状態 $ρ$ が局所次元 $d_A$ と $d_B$ を持ち、シュミット数が $s$ であるならば、次の条件を満たすPSD行列 $ω$ が拡張空間 $AA'B'B$ に存在します。ここで、$A'$ と $B'$ の次元は $s$ であり、$ω / s$ は $AA'|B'B$ に対して分離可能であり、$Π^† ω Π = ρ$ となります。ここで、$Π = 1_A ⊗ s ψ^+ ⊗ 1_B$ であり、$ψ^+$ は正規化されていない最大エンタングル状態です。分離可能性はDPS階層を用いてテストされ、`n` は $B'B$ サブシステムのコピー数を制御します。

参考文献:

  * Hulpke, Bruss, Lewenstein, Sanpera, [arXiv:quant-ph/0401118](https://arxiv.org/abs/quant-ph/0401118)
  * Weilenmann, Dive, Trillo, Aguilar, Navascués, [arXiv:1912.10056](https://arxiv.org/abs/1912.10056)
