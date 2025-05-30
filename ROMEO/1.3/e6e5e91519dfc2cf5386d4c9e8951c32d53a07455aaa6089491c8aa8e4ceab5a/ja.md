```
unwrap(wrapped::AbstractArray; keyargs...)
```

3Dおよび4DデータのためのROMEOアンラッピング。

### オプションのキーワード引数:

  * `TEs`: 4Dデータに必要です。マルチエコーデータのエコー時間。単一エコーアプリケーションの場合、位相と位相2をタプル（例: (5, 10) または [5, 10]）として指定します。
  * `weights`: オプションは [`:romeo`] | `:romeo2` | `:romeo3` | `:bestpath` です。
  * `mag`: 大きさはアンラッピングパスを改善するために使用されます。
  * `mask`: マスク内でのみアンラッピングが実行されます。
  * `phase2`: 2番目の参照位相画像（異なるエコー時間の可能性があります）。位相コヒーレンス重みを計算するために使用されます。これは4Dマルチエコー入力に対して自動的に行われるため、必須ではありません。
  * `correctglobal=false`: `true`の場合、グローバルn2πオフセットを修正します。
  * `individual=false`: `true`の場合、エコーの個別アンラッピングを実行します。詳細については `?unwrap_individual` を入力してください。
  * `template=1`: 空間的にアンラッピングされるエコー（`individual`が`false`の場合）。
  * `maxseeds=1`: 高い値はより多くの別々の領域を許可します。
  * `merge_regions=false`: アンラッピング後に隣接する領域を空間的にマージします。
  * `correct_regions=false`: 各領域の中央値を0に最も近づけるためにn2πを追加します。
  * `wrap_addition=0`: [0;π]、'線形アンラッピング'を許可し、隣接するボクセルがより多くの(π+wrap_addition)位相差を持つことができます。
  * `temporal_uncertain_unwrapping=0.5`: 静脈に便利です。時間的アンラッピング後に高い不確実性値を持つボクセルに対して空間的アンラッピングを使用します。より高い品質の閾値は、より多くのボクセルを空間的に再アンラッピングします。

# 例

```julia-repl
julia> using MriResearchTools
julia> phase = readphase("phase_3echo.nii")
julia> unwrapped = unwrap(phase; TEs=[1,2,3])
julia> savenii(unwrapped, "unwrapped.nii"; header=header(phase))
```
