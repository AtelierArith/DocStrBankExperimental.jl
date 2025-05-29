```
# 1 
@provider function name(arg::Artifact, ...)::Artifact
          ...
end

# 2
@provider name(arg::Artifact, ...)::Artifact = x

# 2
@provider name(Artifact,...)::Artifact

# 3
@provider alias = name(Artifact, ...)::Artifact
```

指定された入力と出力を持つプロバイダーを宣言します。すべての入力 + 出力は一意のアーティファクトでなければなりません。

構文の3つのバージョンがサポートされています：1と2 - 関数定義、3 - 既存の関数をプロバイダーとして宣言、4 - 既存の関数へのエイリアスを作成し、それをプロバイダーとして宣言します。
