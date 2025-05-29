```
QKModel(N::Int, M::Int, mu::AbstractVector, Phi::AbstractMatrix,
        Omega::AbstractMatrix, A::AbstractVector, B::AbstractMatrix,
        C::Vector{<:AbstractMatrix}, D::AbstractMatrix,
        alpha::AbstractMatrix; check_stability::Bool=false) where {T<:Real}

QKModel(state::StateParams, meas::MeasParams; check_stability::Bool=false)
```

二次カルマンフィルタモデルの仕様を作成します。

# 引数

  * `N::Int`: 状態ベクトルの次元
  * `M::Int`: 測定ベクトルの次元
  * `mu::AbstractVector`: 初期状態平均ベクトル (N×1)
  * `Phi::AbstractMatrix`: 状態遷移行列 (N×N)
  * `Omega::AbstractMatrix`: 状態ノイズ共分散行列 (N×N)
  * `A::AbstractVector`: 測定方程式の定数項 (M×1)
  * `B::AbstractMatrix`: 線形測定行列 (M×N)
  * `C::Vector{<:AbstractMatrix}`: 二次測定行列 (MのN×N行列のベクトル)
  * `D::AbstractMatrix`: 測定ノイズ共分散行列 (M×M)
  * `alpha::AbstractMatrix`: 測定誤差の高次モーメントパラメータ (M×M)

# キーワード引数

  * `check_stability::Bool=false`: trueの場合、状態遷移ダイナミクスが安定かどうかをチェックします

# 代替コンストラクタ

2番目のメソッドは、事前に構築されたStateParamsおよびMeasParamsオブジェクトからの構築を可能にします。

# 戻り値

二次カルマンフィルタに必要なすべてのパラメータを含むQKModelオブジェクトを返します。

# 例

```julia
# 直接構築
N, M = 2, 1
model = QKModel(
    N, M,
    [0.0, 0.0],        # mu
    [0.9 0.0; 0.0 0.9], # Phi
    [0.1 0.0; 0.0 0.1], # Omega
    [0.0],              # A
    [1.0 1.0],          # B
    [reshape([1.0 0.0; 0.0 1.0], 2, 2)], # C
    [0.1],              # D
    [0.0]               # alpha
)

# コンポーネントからの構築
state = StateParams(...)
meas = MeasParams(...)
model = QKModel(state, meas)
```

# 注意事項

  * すべての行列はNとMに応じて適切なサイズでなければなりません
  * モデルコンポーネントは拡張状態表現を構築するために使用されます
  * 安定性チェックは、Phiの固有値が単位円内にあることを確認します
