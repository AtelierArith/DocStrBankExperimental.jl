```julia
(1)
function amplitude(c::Complex;
                        func::Function=identity) = func(abs(c))

(2)
function amplitude(A::AbstractArray{T};
                        func::Function=identity) where T<:Complex

(3)
function amplitude(A::TFAnalyticSignal;
                        func::Function=identity)

(4)
function amplitude(𝐀::TFAnalyticSignalVector;
                        func::Function=identity)
```

(1)

複素数の振幅（絶対値）を返します。これはJuliaの[abs](https://docs.julialang.org/en/v1/base/math/#Base.abs)関数に対応します。以下のメソッドとの構文的一貫性のためにここで提供されています。

(2)

複素数配列`Z`の振幅を返します。通常、`Z`は解析信号を保持しており、その場合出力は解析的（瞬時）振幅（エンベロープとも呼ばれる）です。出力は`Z`と同じサイズの実数配列です。

(3)

[TFAnalyticSignal](@ref)オブジェクト`Z`の解析的（瞬時）振幅を持つ実数行列を返します。出力はデータフィールド`Z.y`と同じサイズです。

(4)

(3)と同様ですが、𝐀内のすべての[TFAnalyticSignal](@ref)オブジェクトの振幅行列のベクトルを返します。

~

すべてのメソッドにおいて、オプションのキーワード引数`func`で関数が提供されると、出力に対して要素ごとに適用されます。例えば、

  * `func=x->x^2`を渡すと、二乗が返されます。
  * `func=x->log(x^2)`を渡すと、対数の二乗が返されます。
  * `func=x->decibel(x^2)`を渡すと、デシベル単位のパワーが返されます。

**参照**: [TFAnalyticSignal](@ref)。

**例**:

```julia
using FourierAnalysis, Plots
x=sinusoidal(10, 2, 128, t*4, 0).*sinusoidal(10, 1, 128, t*4, 0)

# 解析信号標準メソッドを使用したベクトルの振幅と位相
y=analyticsignal(x)
a=amplitude(y)
ϕ=phase(y, func=x->(x+π)/2π*50)
plot([x, a, ϕ]; labels=["signal", "amplitude", "phase"])

# `x`がsr/wl Hz未満の周波数にエネルギーを含む場合の挙動を確認
# （`analyticSignal`関数のドキュメントを参照）
y=analyticsignal(x, 64)
a=amplitude(y)
ϕ=phase(y, func=x->(x+π)/2π*50)
plot([x, a, ϕ]; labels=["signal", "amplitude", "phase"])

# アンラップされた位相
# 以下の行は、引数`unwrapdims`がデフォルトで0のため、何も行いません
ϕ2=unwrapPhase(phase(y))
# これが実行されます
ϕ2=unwrapPhase(phase(y); unwrapdims=1)
plot([x, a, ϕ2./25]; labels=["signal", "amplitude", "unwr. phase"])

# 複数の系列を保持するデータ行列の解析信号からの振幅
X=randn(t, 4)
Y=analyticsignal(X)
A=amplitude(Y)
plot(A[:, 1:2])

# 位相
𝛷=phase(Y)
plot(𝛷[:, 1:1])

# アンラップされた位相
𝛷2=unwrapPhase(𝛷; unwrapdims=1)
plot(𝛷2)

# [-1, 1]で表現された位相
𝛷=phase(Y, func=x->(x+π)/2π)
plot(𝛷[:, 1:1])

# 位相の正弦
𝛷=phase(Y, func=sin)
plot(𝛷[:, 1:1])

# 解析信号から振幅と位相を取得
A, 𝛷=polar(Y)
A
𝛷
```
