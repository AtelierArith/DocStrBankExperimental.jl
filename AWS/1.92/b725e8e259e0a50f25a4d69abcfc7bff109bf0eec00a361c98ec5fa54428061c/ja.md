```
(service::QueryService)(
    operation::String, args::AbstractDict{String, <:Any}=Dict{String, Any}();
    aws_config::AbstractAWSConfig=aws_config
)
```

AWSにクエリリクエストを実行します。

# 引数

  * `operation::String`:
  * `args::AbstractDict{String, <:Any}`: リクエストに含める追加の引数

# キーワード

  * `aws_config::AbstractAWSConfig`: リクエストを満たすための資格情報やその他の情報を含むAWSConfig、デフォルト値はグローバル設定です
  * `feature_set::FeatureSet`: この特定のAPI呼び出しのためのオプトイン機能を指定します。

# 戻り値

  * `Tuple`または`Dict`: `args`を通じて`return_headers`が渡された場合、ヘッダーとレスポンスを含むタプルが返されます。それ以外の場合は単に`Dict`が返されます。
