```
AnnotatedProfile(omics, obs, obsindex)
AnnotatedProfile(op, omicsname, obs, obsindex)
```

# 引数

  * `omics::Dict{Symbol,OmicsProfile}`: 名前をキーとしたオミクスプロファイルのコレクション。
  * `op::OmicsProfile`: 単一のオミクスプロファイル。
  * `omicsname::Symbol`: 与えられた `OmicsProfile` の名前。
  * `obs::DataFrame`: 観察のメタ情報を含むデータフレーム。
  * `obsindex::Symbol`: データフレーム `obs` のインデックス。
