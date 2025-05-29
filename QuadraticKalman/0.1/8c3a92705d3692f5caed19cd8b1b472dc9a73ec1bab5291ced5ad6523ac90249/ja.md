```
StateParams(N::Int, mu::AbstractVector{T}, Phi::Union{AbstractMatrix{T}, UniformScaling}, 
            Omega::Union{AbstractMatrix{T}, UniformScaling}; check_stability::Bool=false) where {T<:Real}
```

モデルの状態空間ダイナミクスを表すためのパラメータをカプセル化するStateParamsインスタンスを構築します。

このコンストラクタは、状態遷移コンポーネント（Phi）および状態ノイズコンポーネント（Omega）に対して、明示的な行列とUniformScalingオブジェクトの両方を受け入れます。以下の条件を強制します：   • 状態平均ベクトルmuの長さはNでなければなりません。   • Phiが具体的な行列として提供される場合、N×Nの次元でなければなりません。   • Omegaが具体的な行列として提供される場合も、N×Nの次元でなければなりません。   • オプションとして、check_stabilityフラグがtrueの場合、Phiのスペクトル半径が1 - 1e-6未満であることを確認し、状態遷移ダイナミクスの安定性を保証します。

UniformScaling入力は、互換性を高めるために明示的なN×N行列に変換され、自動微分（AD）やその他の数値計算に対応します。その後、関数は状態共分散行列SigmaをOmega*final * Omega*final'として計算します。

# パラメータ:

  * N::Int: 状態変数の数（状態ベクトルの次元）。
  * mu::AbstractVector{T}: 状態平均ベクトル; その長さは正確にNでなければなりません。
  * Phi::Union{AbstractMatrix{T}, UniformScaling}: 状態遷移行列; 行列またはUniformScalingオブジェクトとして提供されます。
  * Omega::Union{AbstractMatrix{T}, UniformScaling}: 状態ノイズパラメータ; 行列またはUniformScalingオブジェクトとして提供されます。

# キーワード引数:

  * check_stability::Bool=false: trueに設定されている場合、Phiのスペクトル半径が1 - 1e-6未満であることを確認し、安定性を保証します。

# 戻り値:

StateParams{T}インスタンスを返します：     • N: 状態次元。     • mu: 状態平均ベクトル。     • Phi*final: 明示的なN×N状態遷移行列。     • Omega*final: 明示的なN×N状態ノイズ行列。     • Sigma: Omega*final * Omega*final'として計算された状態共分散行列。
