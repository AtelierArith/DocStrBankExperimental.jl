```
ScaleKeepAspect(minlengths) <: ProjectiveTransform
```

`item`の最短辺を`minlengths`にスケールし、元のアスペクト比を保持します。

## 例

```@example
using DataAugmentation, TestImages
image = testimage("lighthouse")
tfm = ScaleKeepAspect((200, 200))
apply(tfm, Image(image))
```
