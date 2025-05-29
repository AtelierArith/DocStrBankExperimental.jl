```
implot(
    img::AbstractArray;
    clims=Percent(99.5),
    stretch=identity,
    cmap=:magma,
    bias=0.5,
    contrast=1,
    wcsticks=true,
    grid=true,
    platescale=1
)
```

配列またはAstroImageMatのデータ値を色の配列にマッピングする読み取り専用ビューを作成します。これは次のように同等です：

```
implot(
    imview(
        img::AbstractArray;
        clims=Percent(99.5),
        stretch=identity,
        cmap=:magma,
        bias=0.5,
        contrast=1,
    ),
    wcsn=1,
    wcsticks=true,
    wcstitle=true,
    grid=true,
    platescale=1
)
```

### 画像レンダリング

データがRGBAピクセル値にどのようにマッピングされるかについては`imview`を参照してください。

### WCSおよび画像座標

WCSヘッダーが設定されたAstroImageが提供されると、目盛りとプロットグリッドはWCS.jlを使用して計算されます。デフォルトでは、最初のWCS座標系を使用します。基になるピクセル座標は、`dims(img)`によって返される値に`platescale`を掛けたものです。これにより、ピクセル座標を使用して線、領域などを重ね描きすることができます。ワールド座標の点のピクセル座標を計算したい場合は、`world_to_pix`を参照してください。

  * `wcsn`（デフォルトは`1`）は、目盛りとグリッドに使用するヘッダー内のWCS変換を選択します
  * `wcsticks`（デフォルトはWCSヘッダーが存在する場合は`true`）は、目盛りとラベルを表示し、ワールド座標を使用してタイトルを表示します
  * `wcstitle`（デフォルトはWCSヘッダーが存在し、`length(refdims(img))>0`の場合は`true`）。キューブをスライスする際に、ピクセル座標の代わりにワールド座標で見えない軸に沿った位置を表示します。
  * `grid`（デフォルトは`true`）は、プロット上にグリッドを表示します。`wcsticks`がtrueの場合はWCS座標を使用し、そうでない場合は`platescale`を掛けたピクセル座標を使用します。
  * `platescale`（デフォルトは`1`）。基になるピクセル座標をスケーリングして重ね描きなどを容易にします。`wcsticks`がfalseの場合、表示されるピクセル座標もスケーリングされます。

### デフォルト

`clims`、`stretch`、および`cmap`のデフォルト値はそれぞれ`extrema`、`identity`、および`nothing`です。これらのデフォルトは、`AstroImages.set_clims!`、`AstroImages.set_stretch!`、および`AstroImages.set_cmap!`を使用して変更できます。
