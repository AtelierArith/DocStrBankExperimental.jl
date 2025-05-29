MeshFileObjectはMeshFileGeometryに似ていますが、単一のジオメトリを表すのではなく、ジオメトリ、マテリアル、テクスチャを含む全体のオブジェクトや、サポートされているファイルタイプのコレクションをロードすることをサポートしています。

サポートされているフォーマット:     * .obj     * .dae (Collada)

メッシュファイルには他のファイル（テクスチャ画像など）への参照が含まれている場合があるため、MeshFileObjectには、メッシュファイルで指定された相対パスを参照ファイルの内容にマッピングする`resources`辞書も含まれています。これらの内容はデータURIを使用して指定されます。例えば：

```
data:image/png;base64,<base-64 encoded data here>
```

`.dae`または`.obj`ファイルからMeshFileObjectを構築すると、resources辞書は自動的にポピュレートされます。
