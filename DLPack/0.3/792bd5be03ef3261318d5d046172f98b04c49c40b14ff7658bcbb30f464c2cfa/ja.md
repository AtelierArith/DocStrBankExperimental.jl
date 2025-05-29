```
from_dlpack(o)
```

`o`がDLPack仕様に従っている場合、`o`内の同じデータを指すゼロコピーの`array::AbstractArray`を返します。行優先順序の配列の場合、結果の配列はすべての次元が逆になります。
