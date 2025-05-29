```
from(name::String)::Supervised
```

フル `name` で識別された監視ノードを返します。

例えば、`mysupervisor` によって監視されているプロセス `mytask` が与えられた場合：

```
supervisor("mysupervisor", [process(mytask)])
```

このとき、`mytask` プロセスのフルネームは `mysupervisor.mytask` です。
