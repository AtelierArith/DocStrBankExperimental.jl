```
testreport(nam::String,ext="")
```

モデル設定 `nam`（または "all"）のために testreport スクリプトを実行し、`ext` で指定された追加オプション（オプション）を使用します。

```
using MITgcmTools
testreport(MITgcm_config(configuration="front_relax"),"-norun")
#testreport(MITgcm_config(configuration="all"),"-norun")
```
