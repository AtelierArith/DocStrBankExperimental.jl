```
ismeuv(wave, hcol[, he1col=hcol*0.1, he2col=0, fano=false]) -> tau
```

### 目的

連続的な星間EUV光学的深さを計算します。

### 説明

EUV光学的深さは、水素とヘリウムの光イオン化から計算されます。

### 引数

  * `wave`: 波長値（アンストローム単位）。有用な範囲は40 - 912 A; 短い波長では金属の不透明度を考慮する必要があり、長い波長では光イオン化はありません。
  * `hcol`: 星間水素コラム密度（cm-2）。
  * `he1col`（オプション）: 中性ヘリウムコラム密度（cm-2）。デフォルトは0.1*hcol（水素コラムの10%）。
  * `he2col`（オプション）: イオン化ヘリウムコラム密度（cm-2）。デフォルトは0。
  * `fano`（オプションのブールキーワード）: このキーワードがtrueの場合、He Iの4つの最も強い自己イオン化共鳴が含まれます。これらの共鳴の形状はFanoプロファイルによって与えられます - Rumph, Bowyer, & Vennes 1994, AJ, 107, 2108を参照してください。これらの共鳴が含まれる場合、入力波長ベクトルは190 Aから210 Aの間で細かい（>~0.01 A）グリッドを持つ必要があります。なぜなら、共鳴は非常に狭いからです。

### 出力

  * `tau`: 結果の光学的深さを与えるベクトル、非負の値。

### 例

波長w（アンストローム単位）のモデルEUVスペクトルがあります。N(HeI)/N(HI) = N(HeII)/N(HI) = 0.05で、1e18 cm-2のHIによるEUV光学的深さを求めます。

```jldoctest
julia> using AstroLib

julia> ismeuv.([670, 910], 1e19, 5e17, 5e17)
2-element Vector{Float64}:
 27.35393320556168
 62.683796028917286
```

### 注意事項

この関数のコードはIDL天文学ユーザーライブラリに基づいています。
