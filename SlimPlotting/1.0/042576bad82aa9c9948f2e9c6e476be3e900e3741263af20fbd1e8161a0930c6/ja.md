```
compare_shots(image1, image2, spacing; perc=98, cmap=:linear_grey_10_95_c0_n256,
              o=(0, 0), interp="hanning", aspect=nothing, d_scale=1.5, side_by_side=false,
              chunksize=20, name="データ一致", units="m", new_fig=true, save=nothing)
```

image1とimage2の2つのショットレコードを比較します。このプロットユーティリティは、2つのモードをサポートしています：`side_by_side`はショットレコードを隣同士にプロットし、2つ目はそのトレースが反転されます。また、`overlap`（デフォルト）では、2つのショットが重なり合い、各ショットから交互に`chunksize`（デフォルト20）のトレースを選択します。

# 引数

  * `image1::Array{T, 2}`: 最初の画像
  * `image2::Array{T, 2}`: 最初の画像と比較する2番目の画像
  * `spacing::Tuple`: 物理単位でのグリッド間隔
  * `perc::Int`: （オプション）クリッピングパーセンタイル、デフォルト=95
  * `cmap::Symbol`: （オプション）カラーマップ、デフォルト=:linear*grey*10*95*c0_n256。`overlap`モード用のカラーマップのタプルを提供できます
  * `o::Tuple`: （オプション）画像の原点、デフォルト=(0, 0)
  * `interp::String`: （オプション）補間方法、デフォルト="hanning"
  * `aspect::Symbol`: （オプション）アスペクト比、デフォルト=:auto
  * `d_scale::Float`: （オプション）深さスケーリング、デフォルト=1.5。適用されるスケーリングは`(1:max_depth).^d_scale`です。
  * `labels::Tuple`: （オプション）軸のラベル、デフォルト=(:X, :Depth)
  * `name::String`: （オプション）図のタイトル、デフォルト="RTM"
  * `units::Tuple(String)`: （オプション）各軸の物理単位、デフォルト=(:m, :m)。
  * `new_fig::Bool`: （オプション）新しい図を作成するか、デフォルト=true
  * `save::String`: （オプション）図をファイルに保存、デフォルト=nothingは図を保存しません
  * `cbar::Bool`: （オプション）カラーバーを表示するか、デフォルト=false
  * `chunksize::Integer`: オーバーラップ比較のためのチャンク内のトレース数
  * `side_by_side::Bool`: サイドバイサイド（true）またはオーバーラップ（false、デフォルト）比較をプロットするかどうか
