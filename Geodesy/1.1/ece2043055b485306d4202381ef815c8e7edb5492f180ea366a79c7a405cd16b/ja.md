```
WGS84()
```

1984年の世界測地系を表すオブジェクトを構築します。これは動的な基準点であり、特定のWGS84フレームに関する詳細は以下を参照してください。

消費者用GPSデバイスから位置情報を取得している場合、デフォルトでWGS84が使用される可能性が高いです。これはGPS衛星が位置を放送する基準点です（「放送エフェメリス」）。ただし、多くのデバイスは国の基準点での位置も提供できるため、デバイスの設定を確認して確かめるべきです。

低精度の作業（おおよそ1メートル未満）の特別なケースとして、`WGS84`はキャプチャ時間なしで提供された座標がGeodesy.jlに知られている*最新の*フレーム実現（WGS84 (G1762)）にあると仮定します。これは、歴史的データを処理している場合や、Geodesy.jl自体が古い場合には正しくない可能性があります。より高い精度が必要な場合は、各座標に対してキャプチャ日付を提供するか、`WGS84`型に`GpsWeek`パラメータを明示的に使用して提供する必要があります：

```
WGS84{GpsWeek}()
```

指定された`GpsWeek`以前に収集されたデータを使用して計算された静的WGS84基準点を表すオブジェクトを構築します。WGS84は、ITRFと0.1m以内で整合させるために、米国国家地理空間情報局（NGA）によって不定期に維持および更新されています（参照：[1]）。そのレベルでの精度が重要な場合は、別の基準点（例えばITRF）で位置を解決することをお勧めします。2016年現在、`GpsWeek`は[0, 730, 873, 1150, 1674, 1762]のいずれかである必要があります。

これらのフレームの実装日付は、衛星によって放送されるGPS週とは異なることに注意してください - 参照：[1]、表2.1。（TODO：特定の日付でどのフレームを使用するかを判断するための表をGeodesyに持たせるべきでしょうか？ 誰か気にしていますか？）

1. "World Geodetic System 1984", NGA標準 NGA.STND.0036*1.0.0*WGS84, 2014-07-08, http://earth-info.nga.mil/GandG/publications/NGA*STND*0036*1*0*0*WGS84/NGA.STND.0036*1.0.0*WGS84.pdf

```
