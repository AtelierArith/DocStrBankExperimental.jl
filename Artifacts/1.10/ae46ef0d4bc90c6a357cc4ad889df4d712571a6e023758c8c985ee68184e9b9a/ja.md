```
macro artifact_str(name)
```

アーティファクトへのディスク上のパスを返します。プロジェクトの `(Julia)Artifacts.toml` ファイルで名前によってアーティファクトを自動的に検索します。要求されたアーティファクトが存在しない場合はエラーをスローします。REPLで実行されると、現在のディレクトリから始めてtomlファイルを検索します。詳細は `find_artifacts_toml()` を参照してください。

アーティファクトが「遅延」とマークされており、パッケージに `using LazyArtifacts` が定義されている場合、このマクロがパスを計算しようとする最初の時に `Pkg` を使用してアーティファクトがオンデマンドでダウンロードされます。その後、ファイルはローカルにインストールされたままにされ、後で使用できます。

`name` にスラッシュ（/）または逆スラッシュ（\）が含まれている場合、最初のスラッシュ以降のすべての要素はアーティファクト内のパス名として扱われ、アーティファクト内の単一のファイル/ディレクトリにアクセスするための簡単なワンライナーが可能になります。例：

```
ffmpeg_path = @artifact"FFMPEG/bin/ffmpeg"
```

!!! compat "Julia 1.3"
    このマクロは少なくともJulia 1.3を必要とします。


!!! compat "Julia 1.6"
    スラッシュインデックスは少なくともJulia 1.6を必要とします。

