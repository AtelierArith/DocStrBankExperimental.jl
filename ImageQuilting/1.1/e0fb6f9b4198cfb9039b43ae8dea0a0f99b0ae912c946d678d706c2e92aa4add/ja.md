```
iqsim(trainimg::AbstractArray{T,N}, tilesize::Dims{N},
      simsize::Dims{N}=size(trainimg);
      overlap::NTuple{N,<:Real}=ntuple(i->1/6,N),
      soft::AbstractVector=[], hard::Dict=Dict(), tol::Real=.1,
      path::Symbol=:raster, nreal::Integer=1,
      debug::Bool=false, showprogress::Bool=true,
      rng::AbstractRNG=Random.default_rng())
```

Hoffimann et al. 2017で説明されている画像キルティングシミュレーションを実行します。

## パラメータ

### 必須

  * `trainimg` は任意のJulia配列です
  * `tilesize` はタイルサイズです

### オプション

  * `simsize` はシミュレーショングリッドのサイズ（デフォルトはトレーニング画像のサイズ）
  * `overlap` はオーバーラップの割合（デフォルトはタイルサイズの1/6）
  * `soft` は `(data,dataTI)` ペアのベクトル（デフォルトはなし）
  * `hard` は座標をデータ値にマッピングする辞書（デフォルトはなし）
  * `tol` は初期緩和許容度 (0,1]（デフォルトは .1）
  * `path` はシミュレーションパス（`:raster`, `:dilation` または `:random`）
  * `nreal` は実現の数（デフォルトは1）
  * `debug` は境界カットとボクセル再利用をエクスポートするかどうかを示します
  * `showprogress` は推定時間の表示をするかどうかを示します
  * `rng` は乱数生成器（デフォルトは `Random.default_rng()`）

主な出力 `reals` は、`reals[1], reals[2], ..., reals[nreal]` でインデックス可能な実現のリストで構成されています。`debug=true` の場合、追加の出力が生成されます：

```julia
reals, cuts, voxs = iqsim(..., debug=true)
```

`cuts[i]` は `reals[i]` の境界カットであり、`voxs[i]` は関連するボクセル再利用です。
