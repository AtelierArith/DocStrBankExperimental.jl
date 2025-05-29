```
gravfft(cmd0::String="", arg1=nothing, arg2=nothing; kwargs...)
```

重力、等静圧、アドミッタンス、およびグリッドのコヒーレンスのスペクトル計算。

## パラメータ

  * **D** | **density** :: [Type => Str | GMTgrid]

    SI単位系での体密度を設定します。定数密度または変動密度のグリッドのいずれかを提供します。
  * **E** | **n_terms** :: [Type => Number]

    パーカー展開に使用される項の数 [デフォルト = 3]。
  * **F** | **field** :: [Type => Str | Tuple]

    希望する重力ポテンシャル場を指定します：重力ではなくジオイドを計算します。
  * **I** | **admittance** :: [Type => Number]

    ingrid2とingrid1（地形/海底地形のあるグリッド）を使用してアドミッタンス|コヒーレンスを推定し、GMTdatasetを返します。
  * **N** | **dimensions** | **inquire** :: [Type => Str]         $Arg = [a|f|m|r|s|nx/ny][+a|[+d|h|l][+e|n|m][+twidth][+v][+w[suffix]][+z[p]]$

    FFTに適したグリッドの次元を選択または問い合わせ、オプションのパラメータを設定します。FFT次元を制御します：
  * **Q** | **flex_topo** | **flexural_topography** :: [Type => Bool]

    フレクシャルトポグラフィを持つグリッドを計算します。
  * **S** | **subplate** | **subplate_load** :: [Type => Bool]

    現在の海底地形と理論モデルによって生成されたサブプレート荷重による予測重力またはジオイドグリッドを計算します。
  * **T** | **topo_load** :: [Type => Str]

    弾性プレートの厚さ `te` に対する地形荷重（入力グリッドファイル）からの等静的補償を計算します。
  * **W** | **level** :: [Type => Number]

    地形に対する水深（または観測高さ）をメートル単位で設定します [0]。kmを示すにはkを追加します。
  * **Z** | **moho_depth** :: [Type => Number]

    モホ [および隆起] の平均補償深度（メートル単位で下向きの正の値）。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。

完全なドキュメントを見るには、次のように入力します： $@? gravfft$

### 例。ゴリンジバンクの重力効果を計算します。

```julia
    G = grdcut("@earth_relief_10m", region=(-12.5,-10,35.5,37.5));
	G2 = gravfft(G, density=1700, F=(faa=6,slab=4), f=:g);
	imshow(G2)
```
