```julia
Constant(; ...) -> PhysicalParticles.Constant
Constant(
    units;
    c_0,
    G,
    h,
    e,
    m_e,
    m_n,
    m_p,
    σ,
    H,
    k_B,
    ε_0,
    μ_0,
    ACC0
) -> PhysicalParticles.Constant

```

基本的な物理定数を `units` に対応して格納する不変構造体を構築します（デフォルトは `uAstro` です）。

## キーワード

  * c:    光の速度
  * G:    ニュートンの万有引力定数
  * m_e:  電子の質量
  * m_n:  中性子の質量
  * m_p:  陽子の質量
  * k_B:  ケルビン・ボルツマン定数
  * ACC0: 修正された重力加速度定数

## 例

```jl
Constant()
Constant(uSI)
Constant(uCGS)
using Unitful
ustrip(Constant())
```
