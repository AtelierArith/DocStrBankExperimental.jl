```
ITRF{Year}([epoch])
```

指定された`Year`の国際地球基準系を表すオブジェクトを構築します。ITRFは、世界中で使用される標準的な高精度の地球基準系です。オプションの`epoch`パラメータは、通常、GPSデバイスを使用して座標が測定された日付など、関心のある時間を定義します。`epoch`パラメータがない場合、結果として得られる`ITRF{Year}`オブジェクトは、完全な動的基準を表します。

*実現*は、衛星および天体測定からの大規模な基準点の位置を計算することによって数年ごとに作成されます。`Year`パラメータは、フレーム処理回帰問題に使用されたデータの最終年を表します。最近の実現のリストは http://itrf.ensg.ign.fr/ITRF_solutions で入手可能です。2016年7月時点で有効な`Year`は2014、2008、2005、2000、1997、1996、1994、1993、1992、1991、1990、1989、1988でした。

技術的な概要については http://itrf.ensg.ign.fr/general.php を参照してください。役立つ技術論文：

  * "IERS Conventions (2010)", Petit and Luzum (eds.), IERS Technical note No.36,  Chapter 4, https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html
  * "ITRF2008: an improved solution of the international terrestrial reference  frame", Altamimi et al., J. Geodesy (2011) 85: 457,  http://dx.doi.org/10.1007/s00190-011-0444-4
  * "IGS08: the IGS realization of ITRF2008", Rebischung et al., GPS Solutions  (2012) 16: 483, http://dx.doi.org/10.1007/s10291-011-0248-2,  ftp://igs.org/pub/resource/pubs/IGS08*The*IGS*Realization*of_ITRF2008.pdf
  * "The IGS contribution to ITRF2014", Rebischung et al., J. Geodesy (2016) 90:  611, http://dx.doi.org/10.1007/s00190-016-0897-6
