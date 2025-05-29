```
modify_model!(ret::Retrofit, config, data, model)
```

レトロフィットのモデルを修正します。すべてのレトロフィットに対して一度だけ発生します。

  * 元の発電機とレトロフィットの容量の合計が元の最大値未満で、元の最小値より大きくなるように制約 `cons_pcap_gen_retro_min` と `cons_pcap_gen_retro_max` を追加します。
  * レトロフィット年の前および当日に対する `cons_pcap_gen_noadd` 制約を削除します。
  * レトロフィット年の前に新しいレトロフィット発電機の容量を0に固定します。
