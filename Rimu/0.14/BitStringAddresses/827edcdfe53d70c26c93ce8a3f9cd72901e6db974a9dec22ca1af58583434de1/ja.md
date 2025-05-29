```
fs"$(string)"
```

フォック状態のコンパクトな表現を解析します。ベクトルからREPLへの出力をコピーするのに便利です。

# 例

```jldoctest
julia> DVec(BoseFS{3,4}(0, 1, 2, 0) => 1)
DVec{BoseFS{3, 4, BitString{6, 1, UInt8}},Int64} with 1 entry, style = IsStochasticInteger{Int64}()
  fs"|0 1 2 0⟩" => 1

julia> fs"|0 1 2 0⟩" => 1 # 上記の出力からコピー
BoseFS{3,4}(0, 1, 2, 0) => 1

julia> fs"|1 2 3⟩⊗|0 1 0⟩" # 複合ボソニックフォック状態
CompositeFS(
  BoseFS{6,3}(1, 2, 3),
  BoseFS{1,3}(0, 1, 0),
)

julia> fs"|↑↓↑⟩" # フェルミオンフォック状態を構築
CompositeFS(
  FermiFS{2,3}(1, 0, 1),
  FermiFS{1,3}(0, 1, 0),
)

julia> s = fs"|0 1 2 0⟩{}" # デフォルトのUInt8コンテナを持つOccupationNumberFSを構築
OccupationNumberFS{4, UInt8}(0, 1, 2, 0)

julia> [s] # 中括弧内に指定された有意なビット数で出力
1-element Vector{OccupationNumberFS{4, UInt8}}:
 fs"|0 1 2 0⟩{8}"
```

[`FermiFS`](@ref)、[`BoseFS`](@ref)、[`CompositeFS`](@ref)、[`FermiFS2C`](@ref)、[`OccupationNumberFS`](@ref)も参照してください。
