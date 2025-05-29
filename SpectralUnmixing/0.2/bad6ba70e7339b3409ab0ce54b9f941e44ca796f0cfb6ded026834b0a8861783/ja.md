```
reduce_endmembers_nmf!(library::SpectralLibrary, max_endmembers_per_class::Int64)
```

スペクトルライブラリ内のエンドメンバーの数を非負行列因子分解（NMF）を使用して削減します。

  * `library.class_valid_keys`内の各クラスに対して、スペクトルのサブセットにNMFを適用して指定された最大数のエンドメンバーを特定します。
  * `library.classes`と`library.spectra`を更新して、削減されたエンドメンバーのセットを含むようにします。

# 注意事項

  * この関数は`library`をその場で変更します。
  * NMF計算では`library.good_bands`のみが考慮されます。
  * NMFは収束のために最大500回の反復を使用し、許容誤差は1.0e-2です。
