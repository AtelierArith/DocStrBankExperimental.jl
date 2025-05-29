```
retrofit!(ret::Retrofit, newgen) -> ::AbstractDict
```

この関数は、`newgen`をレトロフィットのプロパティを持つように変更する必要があります。`newgen`は、元の発電機のすべてのプロパティを含む`Dict`ですが、以下のフィールドがすでに変更されています：

  * `year_retrofit` - レトロフィットされる年に設定
  * `retrofit_original_gen_idx` - 元の発電機のための発電機テーブルのインデックスに設定
  * `capex` - すでに建設された発電機のために二重にcapexを支払わないように0に設定。`newgen`に追加されるcapexは、レトロフィット自体の資本コストのみであるべきです。E4STは、元の発電機のために`past_capex`でcapexをすでに考慮しているはずです。
  * `pcap0` - 0に設定
  * `transmission_capex` - 0に設定
  * `build_status` - `unretrofitted`に設定
