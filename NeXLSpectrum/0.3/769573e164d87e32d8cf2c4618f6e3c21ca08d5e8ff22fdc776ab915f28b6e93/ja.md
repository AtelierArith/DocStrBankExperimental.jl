```
direct(elm::Element, spec::Spectrum, mat::Material=spec[:Composition])
direct(elm::Element, specfile::String, mat::Material)
direct(elm::Element, specfile::String)
```

直接フィット参照を表す構造体を構築します。`references(...)`と共に使用して、未知のスペクトルに対して複数の参照を「直接的」な線形フィットを使用してフィットさせるための参照セットを構築します。
