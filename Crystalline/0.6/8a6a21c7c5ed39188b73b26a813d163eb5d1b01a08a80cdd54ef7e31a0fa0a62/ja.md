```
bandreps(sgnum::Integer, D::Integer=3; 
         allpaths::Bool=false, spinful::Bool=false, timereversal::Bool=true)
```

空間群 `sgnum` と次元 `D` に対して、基本バンド表現 (EBR) を `BandRepSet` として返します。

## キーワード引数

  * `allpaths`: 最小限の十分なセット (`false`, デフォルト) またはすべて (`true`) の **k**-ベクトルを含める。
  * `spinful`: スピンなしおよびスピンありの粒子に適した単一 (`false`, デフォルト) または二重値 (`true`) の不変量表現。 `D=3` の場合のみ利用可能。
  * `timereversal`: 時間反転対称性の存在 (`true`, デフォルト) または不在 (`false`) を仮定する。

## 参考文献

3D EBRは、ビルバオ結晶学サーバーの [BANDREP プログラム](http://www.cryst.ehu.es/cgi-bin/cryst/programs/bandrep.pl) から取得されます。公開された研究で使用する場合は、そこに記載されている元の研究論文を参照してください。
