```
thermo_Psi!(model::Physics{T,F,M,Tu,E,D,BI}, Psif::FaceScalarField) 
where {T,F<:AbstractCompressible,M,Tu,E,D,BI}
```

関数はPsiの値を更新します。

### 入力

  * `model`  – ユーザーによって定義された物理モデル。
  * `Psif`    – 圧縮因子 FaceScalarField。

### アルゴリズム

弱圧縮性は現在、圧縮因子を確立するために理想気体の方程式を使用しています。ここで、$\rho = p * \Psi$です。$\Psi$は、感覚的エンタルピー、基準温度、および流体モデルで指定された$C_p$と$R$値から計算され、$R$は流体モデルで指定された$C_p$と$\gamma$から計算されます。
