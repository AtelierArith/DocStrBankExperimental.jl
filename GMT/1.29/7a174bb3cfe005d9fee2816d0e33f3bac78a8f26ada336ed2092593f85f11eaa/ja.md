```
[GI = ] earthregions(name=""; proj="guess", country=false, dataset="", grid=false,
                     res="", registration="", round=0, exact=false)
```

`earthregions` は、名前付きの地理的地域に対してグリッド/画像をプロットまたは自動的に抽出します。事前定義された地域の大規模なリストは、*コレクション*を介して提供されており、これには名前、長方形の地理的境界、およびそれらにアクセスするためのコードが含まれています。ユーザーは、コードを使用して地域を選択し、その地域の地図を作成するか、その地域のトポ/バチメトリックデータ（グリッドまたは画像）をダウンロードするかを選択します。

### パラメータ

  * `name`: これは、1つのコレクションの名前または1つの地理的地域のコードのいずれかです。コレクション名（次のいずれか: $"DCW", "NatEarth", "UN", "Mainlands", "IHO", "Wiki", "Lakes"$）の場合、そのコレクションの地域が印刷され、地域の境界、コード、および名前が表示されます。代わりにコードが渡された場合（コードは一意です）、`grid` または `dataset` の値に応じて、その地域の地図を生成する（デフォルト）か、グリッド/画像を抽出します。
  * `proj`: 地図が要求される場合、希望する投影をproj4文字列の形式で渡すか、その地図のためのGMT投影構文を使用します。デフォルトでは、地図の制限に基づいて良い投影を推測します。
  * `country`: $DCW$ コレクションの特定のケースでは、国境線をプロットすることもできます。これを行うには `country=true` を設定します。$DCW$ 地域は、カンマ区切りの国コードのリストで指定できます。*例* `earthregions("PT,ES", country=true)`。
  * `dataset`: このオプションは、地図のプロットの代わりにデータのダウンロードを選択するために使用されます。利用可能なデータセットは、https://www.generic-mapping-tools.org/remote-datasets/ で説明されているもので、簡単に言うと: $"earth_relief", "earth_synbath", "earth_gebco", "earth_mask", "earth_day", "earth_night", "earth_geoid", "earth_faa", "earth_mask", "eart_dist", "earth_mss", "earth_vgg", "earth_wdmam", "earth_age", "mars_relief", "moon_relief", "mercury_relief", "venus_relief", "pluto_relief"$。

    $$
    "earth_day", "earth_night"
    $$

    は、サーバーにタイルとして保存されていない画像であるため、ファイル全体がダウンロードされます（初回のみで、ローカルの ~.gmt/server ディレクトリに保存されます）。したがって、初回使用時には時間がかかる場合があります。
  * `grid`: `dataset="earth_relief"` に相当する短縮形のブールオプション
  * `res`: データセットの解像度。可能な解像度は: $"01d", "30m", "20m", "15m", "10m", "06m", "05m", "04m", "03m", "02m", "01m", "30s", "15s", "03s", "01s"$。ただし、すべてのデータセットで利用できるわけではありません。たとえば、すべての解像度に対して存在するのは $"earth_relief", "earth_synbath", "earth_gebco"$ のみです。`dataset` が指定されているが解像度が指定されていない場合、地図の範囲に基づいてその解像度を推定します。
  * `registration`: データセットの登録。`grid` または `pixel`。提供されていない場合は、1つを選択します。
  * `exact`: コレクション内の地域の境界は、より親しみやすい数（少数）に丸められています。これは、純粋な $GMT$ （`coast`）の数値とはわずかに異なることを意味します。`exact=true` を設定すると、厳密な $GMT$ 制限を使用することが強制されます。
  * `round=inc`: 境界を、inc（xinc,yinc）または（winc,einc,sinc,ninc）で示されたステップの倍数に丸めて調整します。さらに、`round` は文字列であることもできますが、その場合は、https://docs.generic-mapping-tools.org/dev/coast.html#r で説明されているハードコアGMT構文に厳密に従う必要があります。

参照: `coast`, `mosaic`

### 戻り値

`dataset` が使用されている場合は $GMTgrid$ または $GMTimage$、それ以外の場合は $nothing$。

## 例

```jldoctest
   earthregions("IHO")                      # IHO によって名付けられた海洋地域のリストを表示

   earthregions("PT,ES,FR", country=true)   # ポルトガル、スペイン、フランス地域の地図を作成。

   G = earthregions("IHO31", grid=true);    # "アゾフ海" のグリッドを取得

   viz(G, shade=true, coast=true)           # そして素敵な地図を作成します。
```

これらの例によって生成されたプロットを見るには、$@? earthregions$ と入力してください。
