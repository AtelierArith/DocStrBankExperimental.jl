```
reduce_endmembers_kmeans!(library::SpectralLibrary, max_endmembers_per_class::Int64)
```

スペクトルライブラリ内のエンドメンバーの数をK-meansクラスタリングを使用して削減します。

  * `library.class_valid_keys`内の各クラスに対して、スペクトルのサブセットにK-meansクラスタリングを適用し、クラスタ中心から指定された最大数のエンドメンバーを特定します。
  * `library.classes`と`library.spectra`を更新して、削減されたエンドメンバーのセットを含むようにします。

# 注意事項

  * この関数は`library`をその場で変更します。
  * K-means計算では、`library.good_bands`のみが考慮されます。
  * K-meansアルゴリズムは最大1000回の反復で実行されます。
