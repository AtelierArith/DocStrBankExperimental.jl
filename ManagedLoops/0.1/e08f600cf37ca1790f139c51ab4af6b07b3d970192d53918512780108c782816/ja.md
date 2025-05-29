```
offload(fun1, mgr::LoopManager, range, args...)
offload(fun2, mgr::LoopManager, (irange, jrange), args...)
```

ループ / ループネストを実行する関数を考えます：

```
    function fun1(range, args...)
        # すべてのインデックス i に共通する計算を行う
        for i irange
            # インデックス i で作業を行う
        end
        return Nothing
    end

    function fun2((irange, jrange), args...)
        # すべてのインデックス i,j に共通する計算を行う
        for j in jrange
            # すべてのインデックス i に共通する計算を行う
            for i irange
                # インデックス i で作業を行う
            end
        end
        return Nothing
    end
```

提供されたマネージャーでループネストを実行します。マネージャーによっては、`fun` が全範囲で一度だけ呼び出される場合や、サブ範囲で何度も呼び出される場合、または単一のインデックスからなる「範囲」で何度も呼び出される場合があります。

!!! warning
    fun() への各呼び出しは独立していなければならず、複数の呼び出しが同時に発生する可能性があります。唯一の保証は、全体の反復空間が重複なくカバーされることです。


!!! note
    `offload` は、上記の例のように、反復間で再利用される結果の前計算のコストを分散させることが*できる*。これは、`offload` がマネージャーによってどのように実装されているかに依存します。

