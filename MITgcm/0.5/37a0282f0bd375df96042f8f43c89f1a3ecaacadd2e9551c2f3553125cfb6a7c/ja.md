```
read_toml(config_name::Symbol)
```

指定された設定名によってtomlパラメータファイルを読み込みます。

```
using MITgcm
params=read_toml(:OCCA2)
```
