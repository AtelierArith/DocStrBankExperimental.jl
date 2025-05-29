```
remotegrid(name, res_p::String=""; res::String="", reg::String="", info=false)
```

他のGMT関数でグリッドを扱う際に便利なGMTの「リモートデータグリッド」のフルネームを生成します。

「リモートデータセット」は、1つ以上のリモートサーバーに保存されているグリッドです。これは、単一のグリッドファイルまたは、より大きなグリッドを構成するサブセットタイルのコレクションである可能性があります。これらはGMTに付属しておらず、インストール手順中にインストールされることもありません。GMTは、リモートファイルメカニズムを介してアクセスできるいくつかのリモートグローバルデータグリッドを提供しています。これらのファイルのいずれかに初めてアクセスすると、GMTは選択したGMTサーバーからファイル（またはサブセットタイル）をダウンロードし、あなたのGMTユーザーディレクトリ[~/.gmt]のサーバーディレクトリに保存します。それ以降は、そこからローカルファイルを読み取ります。詳細については、次を参照してください: https://docs.generic-mapping-tools.org/dev/datasets/remote-data.html#currently-available-remote-data-sets

この関数を使用すると、簡略化された構文を介してGMTの「リモートデータセット」グリッドにアクセスできます。データをダウンロードするのではなく、他のGMT関数で使用できるフルグリッド名を生成して返します（$gmtread$、$grdimage$、$grdcontour$、$grdcut$など）。

### パラメータ

  * `name`: グリッド名。次のいずれか:

      * `earth_age`, `earth_geoid`, `earth_mag`, `earth_gebco`, `earth_gebcosi`, `earth_mask`, `earth_dist`, `earth_faa`, `earth_faaerror`, `earth_edefl`, `earth_ndefl`, `earth_mss`, `earth_mdt`, `earth_relief`, `earth_synbath`, `earth_vgg`, `earth_wdmam`, `earth_day`, `earth_night`,
      * `mars_relief`, `mercury_relief`, `moon_relief`, `pluto_relief`, `venus_relief`.

### キーワード引数

  * `rest_p`または`res`: グリッド解像度。次のいずれかの値: "01d", "30m", "20m", "15m", "10m", "06m", "05m", "04m", "03m"またはそれ以上の高解像度のグリッド。`info`オプションを使用して、グリッドのすべての利用可能な解像度を照会します。接尾辞$d$、$m$、および$s$は、それぞれ弧度、弧分、および弧秒を表します。
  * `reg`: グリッド登録。'g'ridまたは'p'ixel登録のいずれかを選択するか、指定されたものを選択するために空白のままにします。デフォルトでは、ピクセル登録グリッドのみが利用可能な場合を除き、グリッドライン登録グリッドが選択されます。
  * `info`: グリッド情報を印刷する（true）か、フルグリッド名のみを印刷する（false）。`res`オプションと一緒に使用することはできません。

利用可能なグリッド名のリストのみを取得するには、$remotegrid()$と入力します。

上記のように、この関数はデータをダウンロードするものではなく、データをダウンロードする人にとって便利なヘルパーです。ただし、グリッドサイズには非常に注意する必要があります。たとえば、"15s"の$earth_relief$は2.6 GBの重さがあります...そして"01s"では45 GBです。したがって、高解像度のグリッドについては、$grdcut$または$gmtread$によって提供される$region$オプションを使用する必要があります。

### 例

「6m」解像度の月グリッドを表示

```julia
G = gmtread(remotegrid("moon", res="6m"))
viz(G, shade=true)
```

「15s」解像度の「earth_relief」のオマーン上の領域を表示

```julia
G = gmtread(remotegrid("earth_relief", res="15s"), region=(55,60,23,28))
viz(G, shade=true, coast=true)
```

「earth_relief」グリッドのすべての詳細を表示

```julia
@? remotegrid("earth_relief", info=true)
```
