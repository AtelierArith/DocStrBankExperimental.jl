```
mf2comp(material::String, mfs::UncertainValues)::UncertainValues
mf2comp(mat::Material)::UncertainValues
```

`mfs` UncertainValues 構造体で表現された材料組成を、正規化された質量分率、原子分率、平均 Z および平均原子番号を含むいくつかの一般的な表現に変換します。第二の形式は、Material を UncertainValues 形式に変換します。
