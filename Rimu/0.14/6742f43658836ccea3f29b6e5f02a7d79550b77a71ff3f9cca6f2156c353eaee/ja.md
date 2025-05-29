```
@mpi_root expr
```

ルートランクでのみ式を評価します。`expr`には、すべてのMPIランクの同期アクションを必要とするMPI操作を含めてはいけません。

例：

```julia
wn = walkernumber(dv)   # すべてのMPIランクから情報を集めるMPI同期関数呼び出し
                        # 
@mpi_root @info "現在のウォーカーナンバーは" wn # ルートのみで情報メッセージを印刷
```
