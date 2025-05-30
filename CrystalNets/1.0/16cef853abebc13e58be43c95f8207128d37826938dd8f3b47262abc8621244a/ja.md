```
   parse_chemfile(path, options::Options)
   parse_chemfile(path; kwargs...)
```

認識された化学フォーマットで指定されたファイルを解析し、トポロジー情報を抽出します。そのフォーマットは .cif であるか、すべての必要なトポロジー情報を含む Chemfiles.jl によって認識された任意のファイルフォーマットです。
