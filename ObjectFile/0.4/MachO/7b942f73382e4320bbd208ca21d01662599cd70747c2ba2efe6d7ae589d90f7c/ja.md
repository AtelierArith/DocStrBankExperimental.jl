```
MachOSegmentCmd
```

Mach-O セグメントロードコマンドタイプで、プログラムのチャンクの仮想メモリレイアウトに関する情報を含んでいます。このタイプは非常に MachO 特有であるため、他のオブジェクトファイル形式と直接比較することはできません。ただし、このデータ構造はファイルセクションにアクセスするための入り口であり、便利な `Sections(::MachOHandle)` メソッドがすべてを抽象化してくれますが、特定のセグメントに属するセクションを取得するために `Sections(::MachOLoadCmdRef{MachOSegmentCmd})` を直接呼び出すこともできます。`Sections` 呼び出しは `MachOLoadCmdRef{MachOSegmentCmd}` に対してのみ機能し、`MachOSegmentCmd` 自体には直接は機能しません。

### 作成:

  * MachOSegmentCmd()

### フォーマット特有のプロパティ:

  * segment_name()
  * segment_offset()
  * segment*file*size()
  * segment*memory*size()
  * segment*num*sections()
