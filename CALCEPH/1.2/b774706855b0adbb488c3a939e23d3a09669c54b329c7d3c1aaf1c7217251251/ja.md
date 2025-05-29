```
timespan(eph::Ephem)
```

この関数は、ephに関連付けられたエフェメリスファイルで利用可能な最初と最後の時間を返します。

# 引数:

  * `eph` : エフェメリス

# 戻り値:

タプルには以下が含まれます:     * firsttime: 最初の時間のユリウス日     * lasttime: 最後の時間のユリウス日     * continuous: 時間範囲にわたる量の可用性に関する情報

```
    continuousパラメータで次の値が返されます :

    1 すべての天体の量が最初と最後の時間の間の任意の時間に利用可能な場合。
    2 一部の天体の量が最初と最後の時間の間の不連続な時間間隔で利用可能な場合。
    3 各天体の量が最初と最後の時間の間の連続した時間間隔で利用可能であるが、
      最初と最後の時間の間の任意の時間には利用可能でない場合。
```

参照: https://www.imcce.fr/content/medias/recherche/equipes/asd/calceph/html/c/calceph.multiple.html#menu-calceph-gettimespan
