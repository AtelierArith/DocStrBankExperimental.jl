```
testreport(config::MITgcm_config,ext="")
```

モデル `config` のために testreport スクリプトを実行し、必要に応じて `ext` で指定された追加オプションを使用します。

```
using MITgcm
testreport(MITgcm_config(configuration="front_relax"))
#testreport(MITgcm_config(configuration="front_relax"),"-norun")
```
