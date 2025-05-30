未初期化の Pipe オブジェクトを構築します。

パイプの適切な端は、オブジェクトがプロセスの生成に使用されると自動的に初期化されます。これは、プロセスパイプラインで参照を簡単に取得するのに便利です。例えば：

```
julia> err = Pipe()

# この後、`err` は初期化され、`foo` の
# stderr を `err` パイプから読み取ることができます。
julia> run(pipeline(pipeline(`foo`, stderr=err), `cat`), wait=false)
```
