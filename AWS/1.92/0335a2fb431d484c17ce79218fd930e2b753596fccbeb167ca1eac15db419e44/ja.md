```
@service モジュール名 feature=val...
```

`module_name` パラメータに基づいて高レベルのサービスラッパーを含め、オプションで `features` のリストを供給します。

マクロを呼び出すときは、低レベル API の事前定義された定数と一致させることはできません。低レベル API 定数はすべて小文字で命名され、スペースはアンダースコアに置き換えられます。

例:

```julia
using AWS.AWSServices: secrets_manager
using AWS: @service

# これは定数と一致し、エラーになります！
@service secrets_manager
> ERROR: cannot assign a value to variable AWSServices.secrets_manager from module Main

# これはファイル名構造と一致せず、エラーになります！
@service secretsmanager
> ERROR: could not open file /.julia/dev/AWS.jl/src/services/secretsmanager.jl

# 以下のすべての例は有効です！
@service Secrets_Manager
@service SECRETS_MANAGER
@service sECRETS_MANAGER

# 特徴を使用する
@service Secrets_Manager use_response_type = true
```

# 引数

  * `module_name::Symbol`: 高レベル API ラッパーをあなたの名前空間に含めるモジュールとサービスの名前
  * `features=val...`: この高レベル API の含めるために有効/無効にする特徴のリスト。利用可能な特徴のリストについては `FeatureSet` を参照してください。

# 戻り値

  * `Expression`: あなたの名前空間に高レベルサービス API ラッパー関数を埋め込むモジュール
