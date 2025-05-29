```
MeshImportOptions
```

この構造体は、ユーザーがGmsh 4.1 .mshファイルをインポートする際にサポートされている機能を選択できるようにします。

## サポート

  * grouping::Bool | インポート時に2D要素の物理グループ割り当てを含めたいですか？
  * remap*group*name::Bool | インポート時に物理グループIDを維持または再マッピングしたいですか？再マッピングはgroupIdsを1:number*group*idsの範囲にします。
