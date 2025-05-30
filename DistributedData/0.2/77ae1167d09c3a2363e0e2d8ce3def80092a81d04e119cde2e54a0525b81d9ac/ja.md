```
@remote expr
```

リモートワーカーで評価される関数内で、式 `expr`（通常は変数）の評価スコープがリモート側で取得されることを保証し、ローカルセッションとの名前空間の衝突を防ぎます。

これは主に、`Distributed` パッケージの関数（`pmap` や `remotecall` など）が `DistributedData` パッケージによって保存されたデータと連携するために便利です。

内部的には、`eval` でラップすることによって処理されます。

# 例

```
julia> save_at(2, :x, 321)
Future(2, 1, 162, nothing)

julia> let x=123
         remotecall_fetch(() -> x + (@remote x), 2)
       end
444
```
