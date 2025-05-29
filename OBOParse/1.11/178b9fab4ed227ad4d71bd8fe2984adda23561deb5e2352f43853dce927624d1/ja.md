オントロジー用語。

`Term`オブジェクトは、直接非循環オントロジーグラフのノードです。その出力エッジと入力エッジは他のノードとの関係を表し、次のように取得できます。

```julia
relationship(term, sym)
```

および

```julia
rev_relationship(term, sym)
```

それぞれ、ここで`sym`は関係の注釈（例：`:part_of`、`:is_a`、`:regulates`）です。
