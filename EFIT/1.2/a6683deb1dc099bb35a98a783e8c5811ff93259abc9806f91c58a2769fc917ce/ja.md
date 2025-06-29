```
x_points(g::GEQDSKFile)
```

GEQDSKFile構造体内のフラックスマップに基づいてX点を見つけます。X点のR座標、Z座標、正規化されたpsi値のリスト、およびそれらが接続されているセパレトリックス（主=1、二次=2、その他=4）を示すフラグのリストを返します。1、2、または4以外のセパレトリックス値は混乱を示します。

デフォルト設定は調整なしで機能するはずですが、微調整が必要な場合は次のようにします：

neighborhood: ローカル近傍を考慮するために含めるメッシュセルの数; これは、低bpolのゾーンを各領域のローカル最小値を中心にした個別の検索領域に折りたたむためのものです。 bpol*thresh*factor: 一つのX点は明らかにbpolのグローバル最小値の近くにある必要があります。しかし、限られたグリッド解像度のため、次のX点の近くのbpolのローカル最小値はグローバル最小値よりも大きくなります。他の低いbpol値の近くを検索するためには、ある程度の許容範囲が必要です。 psin*tolerance: 主セパレトリックス上のX点を見つけるためのpsinの許容範囲（定義上、psin=1.0であるべきですが、アップサンプリングを行ってもグリッド解像度は無限ではありません）。また、特定された後に追加のX点が二次セパレトリックス上にあるかどうかを判断するためにも使用されます。 within*limiter_only: 制限面内にあるX点のみを探します。
