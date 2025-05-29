```
runtests(args::Vector{String}=ARGS; io::IO=stdout, progname::String=testprogram())
```

テストディレクトリツリー内のいくつかまたはすべてのテストファイルからテストを実行します。

ツリーのルートは、`progname` が存在するディレクトリとして取られます。

テスト名のリストは、`ARGS` が空でない場合は `ARGS` から取得され、それ以外の場合はツリーのルートに対して `testnames` を呼び出すことから取得されます。

テスト名のリストは、その後、各 `@testset` でラップされた `Base.include` を使用してモジュール `Main` に含まれるテストファイル名を構築するために使用されます。
