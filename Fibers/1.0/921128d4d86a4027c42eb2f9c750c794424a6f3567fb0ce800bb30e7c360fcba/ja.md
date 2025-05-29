```
stream(ovec::Union{MRI,Vector{MRI}}; odf::Union{MRI,Nothing}=nothing}, f::Union{MRI,Vector{MRI},Nothing}=nothing, f_thresh::Real=.03, fa::Union{MRI,Nothing}=nothing, fa_thresh::Real=.1, mask::Union{MRI,Nothing}=nothing, lcms::Union{MRI,Nothing}=nothing, lcm_thresh::Real=.099, seed::Union{MRI,Nothing}=nothing, nsub::Union{Integer,Nothing}=3, len_min::Integer=3, len_max::Integer=(isa(ovec,MRI) ? maximum(ovec.volsize) : maximum(ovec[1].volsize)), ang_thresh::Union{Real,Nothing}=45, step_size::Union{Real,Nothing}=.5, smooth_coeff::Union{Real,Nothing}=.2, verbose::Bool=false, search_dist::Integer=15, search_ang::Number=10)
```

ストリームライントラクトグラフィー

# 引数

  * `ovec::Union{MRI,Vector{MRI}}` : 向きベクトル [nvec][nx ny nz 3]

# オプション引数

  * `odf::MRI`                  : ODF [nx ny nz 3 nvert](デフォルト: なし)
  * `f::Union{MRI,Vector{MRI}}` : ベクトル振幅（または体積比）、                               ベクトル単位のマスキング用 [nvec][nx ny nz]
  * `f_thresh::Real`            : 最小ベクトル振幅（または体積比）、                               ベクトル単位のマスキング用 (デフォルト: .03)
  * `fa::MRI`                   : FA（または他の微細構造測定）、                               ボクセル単位のマスキング用 (デフォルト: なし)
  * `fa_thresh::Real`           : 最小FA（または他の微細構造測定）、                               ボクセル単位のマスキング用 (デフォルト: .1)
  * `mask::MRI`                 : 脳マスク [nx ny nz]
  * `seed::Union{MRI,Nothing}`  : シードマスク [nx ny nz](デフォルト: 脳マスクを使用)
  * `nsub::Integer`      : シードボクセルあたりのサブボクセルサンプル数 (デフォルト: 3)
  * `len_min::Integer`   : 最小ストリームライン長 (デフォルト: 3)
  * `len_max::Integer`   : 最大ストリームライン長 (デフォルト: max(nx,ny,nz))
  * `ang_thresh::Real`   : 最大曲がり角度、度単位 (デフォルト: 45)
  * `step_size::Real`    : ステップ長、ボクセル単位 (デフォルト: .5ボクセル)
  * `smooth_coeff::Real` : ベクトルスムージング係数、[0-1]の範囲 (デフォルト: .2)
  * `search_dist::Integer`      : マイクロサーチ距離、ボクセル単位 (デフォルト: 15)
  * `search_ang::Integer`       : マイクロサーチ角度、度単位 (デフォルト: 10)
  * `lcms::Union{MRI,Nothing}`  : LCM (デフォルト: なし) [ny nx nz nmat]
  * `lcm_thresh::Real`          : 最小LCM係数 (デフォルト: .099)
  * `verbose::Bool`      : 伝播方法間の違いをカウント (デフォルト: いいえ)

# 出力

`Tract` 構造体内

  * `.str`: ストリームラインに沿った点のボクセル座標
  * `.scalar`: 方法の違いの指標関数（`verbose==true` の場合のみ）
