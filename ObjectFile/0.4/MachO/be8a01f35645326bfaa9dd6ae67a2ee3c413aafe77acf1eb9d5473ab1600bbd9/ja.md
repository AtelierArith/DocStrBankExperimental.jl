```
MachOLoadCmd
```

Mach-Oオブジェクトファイル内に存在する可能性のあるすべてのロードコマンドに対する抽象化であり、`MachOSegmentCmd`や`MachODySymtabCmd`などのサブクラスを含みます。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装しなければならないメソッドは強調表示されています。

### 作成

  * MachOLoadCmd()
