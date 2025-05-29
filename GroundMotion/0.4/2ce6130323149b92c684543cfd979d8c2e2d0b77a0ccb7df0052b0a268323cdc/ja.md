GMPEモデリング関数からの出力INTENSITYデータのための可変型。INTENSITYはロシアのGOSTR 57546-2017に従った地震スケールです。PGAから簡単に変換できます。`convert_from_pga_to_ssi`関数を参照してください。

フィールド:

```
  lon   :: Float64 
  lat   :: Float64 
  ssi   :: Float64 
```

緯度と経度はWGS84楕円体の度数を想定しています。`ssi`は1.00から12.00までの強度測定値です。
