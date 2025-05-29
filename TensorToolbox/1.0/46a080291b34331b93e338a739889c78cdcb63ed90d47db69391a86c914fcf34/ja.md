---

```
contract(T::TTtensor,X::Array,start_mode,modes)
```

フルテンソル X のモード 1:ndims(X-1) を TTtensor T コア[start*mode:start*mode+modes-1] に収束させます。出力: TTtensor。
