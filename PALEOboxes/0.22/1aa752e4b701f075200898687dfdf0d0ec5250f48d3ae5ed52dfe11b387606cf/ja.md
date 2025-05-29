```
collate_markdown(
    io, inputpath, docspath, src_folderpath; 
    includes=String[], includename="doc_include.jl", imagesdirs=["images"]
) -> (pages::Vector, includes::Vector{String})
```

`inputpath` とサブフォルダを再帰的に検索して:

  * マークダウンファイル（`.md` 拡張子）、
  * `includename` に一致する名前のコードファイル
  * `imagesdirs` に名前が含まれるフォルダ
  * テキストファイル "doc_order.txt"

その後:

  * マークダウンファイルと `imagedirs` 内のフォルダを `<docspath>/src/<src_folderpath>` のサブフォルダにコピーする
  * `Documenter.jl` のツリー構造を構築するのに適した `pages::Vector` を返す。各要素はマークダウンファイルへのパス、または `folder_name => Vector` のペアであり、"doc_order.txt" が存在する場合はそれに従ってソートし、そうでない場合は "README.md" を最初にし、その後は辞書順でソートする。
  * モジュールなどを定義するために含めるべきコードファイルの `includes::Vector` を返す。
