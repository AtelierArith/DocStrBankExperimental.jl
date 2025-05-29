`MatrixCorrection`は、ϕ(ρz)-型行列補正アルゴリズムを計算するための抽象型です。サブクラス`MCA <: MatrixCorrection`は以下を実装する必要があります。

```
# ϕ(ρz)-曲線の下の面積の積分
ℱ(mc::MCA)
# ϕ(ρz)-曲線の下の透過面積の積分
ℱχ(mc::MCA, xray::CharXRay, θtoa::AbstractFloat)
# 透過したϕ(ρz)-曲線の下の0からτまでの面積
ℱχp(mc::MCA, xray::CharXRay, θtoa::AbstractFloat, τ::AbstractFloat)
# ϕ(ρz)-曲線
ϕ(mc::MCA, ρz)
# MCAからのファクトリーメソッド
matrixcorrection(::Type{MCA}, mat::Material, ashell::AtomicSubShell, e0)::MCA
```

アルゴリズムは、`Material`、`AtomicSubShell`およびビームエネルギーに基づいて可能な限り多くの事前計算を行うべきです。クラス`MCA`は、入力値を格納するためにメンバ変数`subshell::AtomicSubShell`、`material::Material`および`E0::AbstractFloat`を定義する必要があります。例として`XPP`を参照してください。

これらのメソッドから、`Z(...)`、`A(...)`のような他のメソッドが実装されます。
