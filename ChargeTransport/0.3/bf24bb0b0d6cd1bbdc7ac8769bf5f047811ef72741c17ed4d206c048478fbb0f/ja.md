```julia
mutable struct System
```

ドリフト拡散型システムに必要なすべての情報を保持する構造体です。

  * `data::ChargeTransport.Data`: すべてのデータ情報を保持する構造体、Dataを参照してください。
  * `fvmsys::VoronoiFVM.AbstractSystem`: 有限体積システムのシステム情報を保持する構造体です。
