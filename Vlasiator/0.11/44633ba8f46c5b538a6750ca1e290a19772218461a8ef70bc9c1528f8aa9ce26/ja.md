```
getlevel(meta::MetaVLSV, cid::Int) -> Int
```

与えられたセルID `cid` のAMRレベルを返します。

!!! warning
    この関数は、`meta` のVLSVファイルが実際に `cid` を含んでいるかどうかを確認しません。これは、洗練された子によって隠されている可能性があります。

