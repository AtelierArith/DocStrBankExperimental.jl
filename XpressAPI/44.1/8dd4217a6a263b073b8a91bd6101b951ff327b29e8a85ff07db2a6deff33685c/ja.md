```
XPRS_BARPERTURB
```

ニュートンバリア：数値的に困難なケースでは、KKTシステムに摂動を適用してその数値特性を改善することがしばしば有利です。（ダブル）

`BARPERTURB` は、バリア反復中に許可される摂動の量を制御します。デフォルトでは、摂動は許可されていません。このパラメータは注意して設定してください。大きな摂動は効率の悪い反復を引き起こす可能性があり、最適な設定は問題に依存します。

デフォルト値： `0`

ドメイン： 0~+INF
