```
G = LQGProblem(sys::ExtendedStateSpace, Q1, Q2, R1, R2; qQ=0, qR=0, SQ=nothing, SR=nothing)
```

LQGオブジェクトを返し、プロセス`sys=ss(A,B,C,D)`の周りの閉ループ制御を記述します。このコントローラはLQGタイプです。コントローラは、状態の偏差と制御信号の分散をそれぞれペナルティとして与える重み行列`Q1,Q2`と、状態のドリフトと測定の共分散をそれぞれ指定する共分散行列`R1,R2`によって指定されます。

`sys`は拡張状態空間オブジェクトであり、上部チャネルは性能変数への外乱（w→z）に対応し、下部チャネルは入力から出力（u→y）に対応します。したがって、`lft(sys, K)`は外部入力/外乱から性能変数への閉ループ伝達関数を形成します。

`qQ`と`qR`はループ伝達回復を組み込むために設定できます。すなわち、

```julia
L = lqr(A, B, Q1+qQ*C'C, Q2)
K = kalman(A, C, R1+qR*B*B', R2)
```

`qQ`を増加させると出力方向のコストが増加し、安価な制御の使用を促進します。一方、`qR`を増加させると架空の動的ノイズが追加され、制御する方向でオブザーバーが速くなります。

# 例

この例では、1つの不安定な極と1つの不安定な零点を持つMIMOシステムを制御します。システムが不安定な零点と極の両方を持つ場合、性能には根本的な制限があります。この場合、不安定な零点は不安定な極よりも速いため、システムは制御可能です。良好な性能を得るためには、不安定な零点の動的特性と不安定な極との間にできるだけ大きな隔たりを持つことが望ましいです。

```julia
s = tf("s")
P = [1/(s+1) 2/(s+2); 1/(s+3) 1/(s-1)]
sys = ExtendedStateSpace(ss(P)) # 制御出力は測定出力と同じで、状態ノイズは入力にのみ影響します。
eye(n) = Matrix{Float64}(I,n,n) # 便利のために

qQ = 0
qR = 0
Q1 = 10eye(2)
Q2 = 1eye(2)
R1 = 1eye(2)
R2 = 1eye(2)

G = LQGProblem(sys, Q1, Q2, R1, R2, qQ=qQ, qR=qR)

T = comp_sensitivity(G)
S = sensitivity(G)
Gcl = closedloop(G)*static_gain_compensation(G)
plot(
    sigmaplot([S,T, Gcl],exp10.(range(-3, stop=3, length=1000)), lab=["S" "T" "Gry"]),
    plot(step(Gcl, 5))
)
```

# 拡張ヘルプ

`LQGProblem`のインスタンスに対していくつかの関数が定義されています。

  * [`closedloop`](@ref)
  * [`extended_controller`](@ref)
  * [`ff_controller`](@ref)
  * [`gangoffour`](@ref)
  * [`G_CS`](@ref)
  * [`G_PS`](@ref)
  * [`input_comp_sensitivity`](@ref)
  * [`input_sensitivity`](@ref)
  * [`output_comp_sensitivity`](@ref)
  * [`output_sensitivity`](@ref)
  * [`system_mapping`](@ref)
  * [`performance_mapping`](@ref)
  * [`static_gain_compensation`](@ref)
  * [`gangoffourplot`](@ref)
  * [`kalman`](@ref)
  * [`lft`](@ref)
  * [`lqr`](@ref)
  * [`observer_controller`](@ref)

LQGインターフェースの使用方法に関するビデオチュートリアルは[こちら](https://youtu.be/NuAxN1mGCPs)で入手できます。

## 参照の導入

参照を導入する最も原則的な方法は、拡張状態空間モデルに測定入力として参照を追加し、性能出力`z`を参照が提供される出力との違いとすることです。

より簡便な方法は、`LQGProblem`を構築する際に参照を考慮せず、代わりに`extended_controller`に`z`キーワード引数を渡して、状態参照から制御出力への閉ループシステムを取得し、このシステム（またはそのサブシステムの1つ）のDCゲインの逆数のいずれかを使用して参照入力を事前補償することです。
