```
ScaleKeepAspect(minlengths) <: ProjectiveTransform
```

Scales the shortest side of `item` to `minlengths`, keeping the original aspect ratio.

## Examples

```@example
using DataAugmentation, TestImages
image = testimage("lighthouse")
tfm = ScaleKeepAspect((200, 200))
apply(tfm, Image(image))
```
