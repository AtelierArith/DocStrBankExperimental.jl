```
get_pheno(dataset::String;gn_url::String=gn_url())
```

指定された `dataset` の非オミクス（「臨床」）表現型を返します。

---

```
get_pheno(dataset::String,trait::String; gn_url::String=gn_url())
```

`group` 内の指定された `trait` を返します。
