```
TAAFT(fϵ)
```

振幅調整フーリエ変換サロゲートの切り捨てバージョン[^Theiler1991][^Nakamura2006]。

切り捨てパラメータと位相ランダム化手順は[`TFTS`](@ref)と同じですが、ここでは元のデータに戻すための追加のステップが実行されます。これにより、元のデータの振幅分布が保持されます。

[^Theiler1991]: J. Theiler, S. Eubank, A. Longtin, B. Galdrikian, J. Farmer, 時系列における非線形性のテスト: サロゲートデータの方法, Physica D 58 (1–4) (1992) 77–94.

[^Nakamura2006]: Nakamura, Tomomichi, Michael Small, and Yoshito Hirata. "長期的トレンドを持つ不規則な変動における非線形性のテスト." Physical Review E 74.2 (2006): 026205.
