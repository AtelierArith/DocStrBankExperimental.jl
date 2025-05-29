```
convertDomain!(g::GirfEssential)
```

周波数領域のGIRFを時間領域に変換し、その逆も行います。また、依存するパラメータも計算します。

# 引数

  * g::GirfEssential - 入力GirfEssentialオブジェクト; 変換タイプはg.isFreqDomainGirfによって決定されます。

# 出力

  * g::GirfEssential - 変換/計算されたフィールドを持つ修正されたGirfEssentialオブジェクト。

この関数は、MATLABにおけるGIRF計算と応用のためのコードパッケージの一部から作成されました。このパッケージはBSD 3条項ライセンスの下で利用可能です。詳細情報は次を参照してください: https://github.com/MRI-gradient/girf 元のMATLAB著者:   Johanna Vannesjo (johanna.vannesjo@gmail.com) 著作権 (C) 2014 IBT, チューリッヒ大学およびETHチューリッヒ,               2016 FMRIBセンター, オックスフォード大学 ```
