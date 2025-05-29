```
place(A, B, p, opt=:c; direct = false)
place(sys::StateSpace, p, opt=:c; direct = false)
```

行列 `K` を計算して、`A - BK` の固有値が `p` になるようにします。

```
place(A, C, p, opt=:o)
place(sys::StateSpace, p, opt=:o)
```

行列 `L` を計算して、`A - LC` の固有値が `p` になるようにします。

`direct = true` で `opt = :o` の場合、観測器ゲイン `K` は `A - KCA` の固有値が `p` になるように計算されます。このオプションは、[`observer_controller`](@ref) で `direct = true` と一緒に使用する必要があります。

注意: `direct = true` は離散時間システムにのみ適用してください。

参考: "Computer-Controlled Systems" pp 140.

SISO システムにはアッカーマンの公式を使用し、MIMO システムには [`place_knvd`](@ref) を使用します。

この関数は数値的に敏感である可能性があるため、拡張精度で配置問題を解決することが有益かもしれません。
