```
print_connectivity(qpu::AbstractQPU, io::IO = stdout)
```

`qpu`のキュービット接続性を`io`に出力します。

# 例

```jldoctest
julia> qpu = AnyonYukonQPU(
           host = "http://example.anyonsys.com",
           user = "test_user",
           access_token = "not_a_real_access_token",
           project_id = "test-project",
           realm = "test-realm"
       )
量子処理ユニット:
   製造元:  Anyon Systems Inc.
   世代:    Yukon
   シリアル番号: ANYK202201
   プロジェクトID:    test-project
   キュービット数:   6
   接続タイプ:  線形
   領域:         test-realm


julia> print_connectivity(qpu)
1──2──3──4──5──6

```
