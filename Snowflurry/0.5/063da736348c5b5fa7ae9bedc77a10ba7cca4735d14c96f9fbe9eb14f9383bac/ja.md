```
AnyonYamaskaQPU <: AbstractQPU
```

ヤマスカ世代のアニオンシステムQPUを記述するデータ構造です。QPUは2D格子配置で24量子ビットを含んでいます（[`LatticeConnectivity`](@ref)を参照）。

# フィールド

  * `client                  ::Client` – QPUサーバーへのクライアント。
  * `status_request_throttle ::Function` – ジョブステータスリクエストのレートを制限するために使用されます。
  * `project_id              ::String` – QPUに送信されるジョブのプロジェクトを識別するために使用されます。
  * `realm                   ::String` – オプション: リクエストの送信のためのホストサーバーの領域を識別するために使用されます。

# 例

```jldoctest
julia>  qpu = AnyonYamaskaQPU(
            host = "http://example.anyonsys.com",
            user = "test_user",
            access_token = "not_a_real_access_token",
            project_id = "test-project",
            realm = "test-realm"
        )
Quantum Processing Unit:
   manufacturer:  Anyon Systems Inc.
   generation:    Yamaska
   serial_number: ANYK202301
   project_id:    test-project
   qubit_count:   24 
   connectivity_type:  2D-lattice
   realm:         test-realm
```
