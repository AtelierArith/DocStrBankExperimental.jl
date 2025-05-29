`pprint` と `pformat` の実装。

次のようなボイラープレートを使用して、きれいな印刷サポートを拡張できます：

```
    function PrettyPrint.pp_impl(io, data::YourType, indent::Int)
        print(io, data)
    end
```
