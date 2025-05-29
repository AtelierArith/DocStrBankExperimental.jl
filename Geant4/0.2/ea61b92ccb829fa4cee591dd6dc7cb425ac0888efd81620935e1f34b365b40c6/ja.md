```
G4JLDetectorGDML(gdmlfile::String; check_overlap::Bool, validate_schema::Bool, init_method::Union{Function,Nothing})
```

GDMLファイルからG4JLDetectorを初期化します。この時点でGDMLファイルが解析されます。

# 引数

  * `gdmlfile::String`: GDMLファイル名
  * `check_overlap::Bool=false`: オーバーラップをチェックする
  * `validate_schema::Bool=true`: スキーマを検証する
  * `init_method::Union{Function,Nothing}=nothing`: 検出器が構築されるときに呼び出される初期化メソッド
