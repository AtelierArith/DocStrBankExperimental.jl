```
udgrade(input_map::HealpixMap{T,O,AA}, output_nside; kw...) where {T,O,AA} -> HealpixMap{T,O,AA}
```

マップをターゲットの nside にアップグレードまたはダウングレードします。常にコピーを作成します。ネストされた順序の場合は非常に高速ですが、リングの場合は最初にネストされた順序に変換する必要があるため遅くなります。

# 引数:

  * `input_map::HealpixMap{T,O,AA}`: アップグレード/ダウングレードするマップ
  * `output_nside`: 希望する nside

# キーワード:

  * `threshold=abs(1e-6UNSEEN)`: 悪いピクセルを UNSEEN と識別するための絶対許容誤差
  * `pess=false`: false の場合、ダウングレード時に残りの良いピクセルからピクセルを推定します。 true の場合、ダウングレードされたピクセル全体が UNSEEN に設定されます。

# 戻り値:

  * `HealpixMap{T,O,AA}`: 入力と同じ順序のアップグレード/ダウングレードされたマップ

# 例

```julia-repl
julia> A = HealpixMap{Float64, NestedOrder}(ones(nside2npix(4)))
192-element HealpixMap{Float64, RingOrder, Vector{Float64}}:
 1.0
 ⋮
 1.0

julia> Healpix.udgrade(A, 2)
48-element HealpixMap{Float64, NestedOrder, Vector{Float64}}:
 1.0
 ⋮
 1.0
```
