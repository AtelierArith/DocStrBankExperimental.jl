```
@iso(using_or_import_statement)
@iso(using_or_import_statement, version_string)
```

パッケージまたは指定されたバージョンのパッケージをロードします。現在、一度に複数のパッケージをロードすることはサポートされていません。

# 例

```
#Globをロードする（`IsoPkg.add("Glob")`の後）
@iso using Glob

#UnicodePlots v1.2.0をロードする（`IsoPkg.add("UnicodePlots@1.2.0")`の後）
@iso using UnicodePlots "1.2.0"
```

---

```
@iso(pkg_name, statement)
```

`pkg_name`環境で`statement`を実行します。

# 例

```
#Glob v1.2.0をロードする（`IsoPkg.add("Glob@1.2.0")`の後；`@iso using Glob "1.2.0"`と同等）
@iso "Glob@1.2.0" using Glob

#Globをテストする
@iso "Glob@1.2.0" Pkg.test("Glob")

#Globのステータスを表示する（`IsoPkg.status("Glob@1.2.0")`と同等）
@iso "Glob@1.2.0" pkg"status --manifest"
```
