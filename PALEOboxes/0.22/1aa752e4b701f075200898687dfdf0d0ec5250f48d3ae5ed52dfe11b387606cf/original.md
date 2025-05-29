```
collate_markdown(
    io, inputpath, docspath, src_folderpath; 
    includes=String[], includename="doc_include.jl", imagesdirs=["images"]
) -> (pages::Vector, includes::Vector{String})
```

Recursively look through `inputpath` and subfolders for:

  * markdown files (`.md` extension),
  * code files with name matching `includename`
  * folders with name in `imagesdirs`
  * a text file "doc_order.txt"

and then:

  * copy markdown files and folders in `imagedirs` to subfolders under `<docspath>/src/<src_folderpath>`
  * return a `pages::Vector` suitable to build a tree structure for `Documenter.jl`, where each element is either a path to a markdown file, or a pair `folder_name => Vector`, sorted according to "doc_order.txt" if present, or otherwise with "README.md" first and then in lexographical order.
  * return an `includes::Vector` of code files that should be included to define modules etc
