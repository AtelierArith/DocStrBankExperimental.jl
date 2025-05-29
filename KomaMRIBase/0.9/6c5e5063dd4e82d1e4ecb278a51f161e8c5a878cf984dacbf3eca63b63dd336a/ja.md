```
obj = brain_phantom3D(; ss=4, us=1, start_end=[160,200])
```

3次元脳ファントム構造体を作成します。デフォルトのss=4サンプリング間隔は2 mmです。元のファイル（ss=1）のサンプリング間隔は0.5 mmです。

# 参考文献

  * B. Aubert-Broche, D.L. Collins, A.C. Evans: "A new improved version of the realistic   digital brain phantom" NeuroImage, in review - 2006
  * B. Aubert-Broche, M. Griffin, G.B. Pike, A.C. Evans and D.L. Collins: "20 new digital   brain phantoms for creation of validation image data bases" IEEE TMI, in review - 2006
  * https://brainweb.bic.mni.mcgill.ca/brainweb/tissue*mr*parameters.txt

# キーワード

  * `ss`: (`::Integer or ::Vector{Integer}`, `=4`) スカラーの場合はすべての軸のサブサンプリングパラメータ、3要素ベクトル[ssx, ssy, ssz]の場合は各軸のサブサンプリングパラメータ
  * `us`: (`::Integer or ::Vector{Integer}`, `=1`) スカラーの場合はすべての軸のアップサンプリングパラメータ、3要素ベクトル[usx, usy, usz]の場合は各軸のアップサンプリングパラメータ
  * `start_end`: (`::Vector{Integer}`, `=[160,200]`) プリサンプリングされたファントムのzインデックス範囲、180が中心

# 戻り値

  * `obj`: (`::Phantom`) 3Dファントム構造体

# 例

```julia-repl
julia> obj = brain_phantom3D(; ss=5)

julia> obj = brain_phantom3D(; us=[2, 2, 1])

julia> plot_phantom_map(obj, :ρ)
```
