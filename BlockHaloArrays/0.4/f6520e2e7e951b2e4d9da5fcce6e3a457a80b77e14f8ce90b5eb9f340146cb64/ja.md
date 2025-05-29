ブロックされた配列構造で、スレッド固有のデータをブロックに格納します。これにより、共有メモリアプリケーションのためのマイクロドメイン分解が促進されます。各スレッドは自分のデータブロックで操作を行います。これにより、マルチスレッドループよりもパフォーマンスのスケーリングが向上します。

# フィールド

  * `blocks::Vector{AA}`:
  * `block_layout::NTuple{D,Int}`: 各次元に沿ったブロックの数
  * `global_blockranges::Array{NTuple{D,UnitRange{Int}},D}`: グローバルな視点から見た各ブロックのインデックス/範囲
  * `nhalo::Int`: ハロー領域の数、例えば各次元に沿って2つのエントリ
  * `loop_limits::Vector{Vector{Int}}`: 便利のためのループ制限、例えば `[ilo,ihi,jlo,jhi]`
  * `globaldims::NTuple{D,Int}`: 単純な `Array{T,D}` であった場合の配列の次元、例えば `(20,20)`
