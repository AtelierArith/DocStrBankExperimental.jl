```
plotchains(
    chain, planet_key;
    N=1500,
    ii = rand(1:size(chain,1)*size(chain,3), N),
    color=length(model.system.planets) == 0 || !haskey(chain, string(planet_key)*"_a") ? nothing : string(planet_key)*"_a",
    colorbartitle=color,
    clims=nothing,
    cmap=:plasma,
    alpha=30/length(ii),
    attime=nothing,
    kwargs...,
)
```

与えられた惑星の名前 `planet_key` に対してポスタリオーチェーンからサンプルを描画し、何らかの方法で可視化します。`kind` を使用して作成するプロットの種類を制御します。いくつかのオプション: :astrometry, :radvel, :trueanom, :meananom, :eccanom, :x, :y, :z, (:x, :y), :raoff, :decoff, :pmra, :pmdec, :accra, :accdec, :radvel, :posangle, :projectedseparation。詳細については PlanetOrbits のドキュメントを参照してください。

入力:

  * chain                   描画するためのチェーン
  * planet_key              モデル内の惑星名 (シンボル)
  * N=1500                  プロットのために描画するサンプル数
  * kind=nothing            作成するプロットの種類を指定します。
  * ii=...                  使用する特定の行番号。例えば、いくつかの異なるプロットで同じ100サンプルを描画したい場合
  * color="planet*key*a"   色をマッピングするための列名。デフォルトでは半長軸ですが、任意の列または任意の配列にすることができます。
  * colorbartitle=color     カラーバーの名前
  * clims=nothing           色の制限のタプル (最小値と最大値)
  * cmap=:plasma            カラーマップ
  * alpha=...               線の透明度
