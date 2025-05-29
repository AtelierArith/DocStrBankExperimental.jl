```
MeasParams(M::Int, N::Int, A::AbstractVector{T}, 
           B::Union{AbstractMatrix{T}, UniformScaling},
           C::Vector{<:Union{AbstractMatrix{T}, UniformScaling}}, 
           D::Union{AbstractMatrix{T}, UniformScaling},
           alpha::Union{AbstractMatrix{T}, UniformScaling}) where {T<:Real}
```

二次状態空間モデルの測定方程式のパラメータを含むMeasParamsオブジェクトを構築します。

# 引数

  * M::Int: 測定変数の数。
  * N::Int: 状態変数の数。
  * A::AbstractVector{T}: 測定方程式の切片項のベクトル。長さはMと等しくなければなりません。
  * B::Union{AbstractMatrix{T}, UniformScaling}: 状態ベクトルを測定空間にマッピングする行列。UniformScalingとして提供された場合、M×N行列に変換されます。
  * C::Vector{<:Union{AbstractMatrix{T}, UniformScaling}}: 二次測定パラメータを表す行列のベクトル。M個の行列が必要で、それぞれのサイズはN×Nです。UniformScaling入力はそれに応じて変換されます。
  * D::Union{AbstractMatrix{T}, UniformScaling}: 測定ノイズをスケーリングする行列で、M×Mである必要があります。UniformScaling入力は標準行列に変換されます。
  * alpha::Union{AbstractMatrix{T}, UniformScaling}: 測定方程式における自己回帰成分をキャプチャする行列。UniformScalingとして提供された場合、M×M行列に変換されます。

# 戻り値

タイプTでパラメータ化されたMeasParamsオブジェクトを返し、測定モデルのすべてのパラメータと、測定ノイズの共分散構造を表すV = D*final * D*final'として計算された補助行列をカプセル化します。

# 詳細

この関数は、すべての入力が具体的な行列として表現されることを保証します。BおよびCの各要素、Dおよびalphaについて、入力がUniformScalingの場合、適切な次元（Bの場合はM×N、Cの各Ciの場合はN×N、Dおよびalphaの場合はM×M）を持つ完全な行列に変換されます。この変換により、正確な線形代数計算のために完全な行列表現が必要なフィルタリングおよびスムージングルーチンでの下流操作との互換性が保証されます。
