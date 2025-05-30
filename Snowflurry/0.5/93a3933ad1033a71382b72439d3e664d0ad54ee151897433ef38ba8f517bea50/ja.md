```
AnyonYukonQPU <: AbstractQPU
```

ユコン世代のアニオンシステムQPUを説明するデータ構造です。QPUは、線形配置で6つのキュービットを含んでいます（[`LineConnectivity`](@ref）を参照）。

# フィールド

  * `client                  ::Client` – QPUサーバーへのクライアント。
  * `status_request_throttle ::Function` – ジョブステータスリクエストのレートを制限するために使用されます。
  * `project_id              ::String` – QPUに送信されるジョブのプロジェクトを識別するために使用されます。
  * `realm                   ::String` – オプション: リクエストの送信のためのホストサーバーの領域を識別するために使用されます。

# 例

```jldoctest
julia>  qpu = AnyonYukonQPU(
            host = "http://example.anyonsys.com",
            user = "test_user",
            access_token = "not_a_real_access_token",
            project_id = "test-project",
            realm = "test-realm"
        )
Quantum Processing Unit:
   manufacturer:  Anyon Systems Inc.
   generation:    Yukon
   serial_number: ANYK202201
   project_id:    test-project
   qubit_count:   6 
   connectivity_type:  linear
   realm:         test-realm
```
