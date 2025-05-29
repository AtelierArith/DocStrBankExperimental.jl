```
reduce_endmembers_pca!(library::SpectralLibrary, max_endmembers_per_class::Int64)
```

スペクトルライブラリ内のエンドメンバーの数を主成分分析（PCA）を使用して削減します。

  * `library.class_valid_keys`内の各クラスに対して、スペクトルのサブセットにPCAを適用して指定された最大数のエンドメンバーを特定します。
  * `library.classes`と`library.spectra`を更新して、削減されたエンドメンバーのセットを含めます。

# 注意事項

  * この関数は`library`をその場で変更します。
  * PCA計算では`library.good_bands`のみが考慮されます。
  * PCAは各エンドメンバークラスごとに`max_endmembers_per_class`のPCに切り捨てられます。
