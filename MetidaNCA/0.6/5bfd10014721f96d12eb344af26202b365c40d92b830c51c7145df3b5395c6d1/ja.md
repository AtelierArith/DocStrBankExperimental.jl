```
nca!(data::PDSubject{T,O}; calcm = :lint, intpm = nothing, verbose = 0, warn = true, io::IO = stdout, modify! = identity, kwargs...) where T where O
```

非区画（NCA）解析薬力学データ。

結果：

  * Rmax - 最大応答;
  * Tmax - 最大応答までの時間;
  * AUCABL - ベースライン上のAUC;
  * AUCBBL - ベースライン下のAUC;
  * AUCATH - 閾値上のAUC;
  * AUCBTH - 閾値下のAUC;
  * AUCNETB - AUCABL - AUCBBL;
  * AUCNETT - AUCATH - AUCBTH;
  * TABL - ベースライン上の時間;
  * TBBL - ベースライン下の時間;
  * TATH - 閾値上の時間;
  * TBTH - 閾値下の時間;
  * AUCBTW - ベースラインと閾値の間のAUC;
