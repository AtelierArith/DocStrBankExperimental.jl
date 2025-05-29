```
@testitem "name" [tags=[] setup=[] retries=0 skip=false default_imports=true] begin
    # テストとして実行されるコード
end
```

単一の独立して実行可能なテストグループ。

テストアイテムは独立したテストのブロックであり、周囲のスコープから名前にアクセスすることはできません。複数のテストアイテムは並行して実行され、分散プロセスで実行されます。

`@testitem` は単一のテストを含むことができます：

```
@tesitem "Arithmetic" begin
    @test 1 + 1 == 2
end
```

または、多くのテストを含むことができ、`@testsets` に配置することができます：

```
@testitem "Arithmetic" begin
    @testset "addition" begin
        @test 1 + 2 == 3
        @test 1 + 0 == 1
    end
    @testset "multiplication" begin
        @test 1 * 2 == 2
        @test 1 * 0 == 0
    end
    @test 1 + 2 * 2 == 5
end
```

`@testitem` は実行時にモジュールにラップされるため、追加のパッケージをインポートする必要があります：

```
@testitem "Arithmetic" begin
    using LinearAlgebra
    @testset "multiplication" begin
        @test dot(1, 2) == 2
    end
end
```

テストアイテムのコードは新しいモジュールのトップレベルコードとして実行されるため、インポートを含めたり、新しい構造体やヘルパー関数を定義したり、テストやテストセットを宣言したりできます。

```
@testitem "DoCoolStuff" begin
    function do_really_cool_stuff()
        # ...
    end
    @testset "cool stuff doing" begin
        @test do_really_cool_stuff()
    end
end
```

デフォルトでは、`Test` とテストされるパッケージは `@testitem` にロードされます。これは `default_imports=false` を渡すことで無効にできます。

`@testitem` は、`@testsetup` で宣言されたテスト特有のセットアップコードを使用することができ、`setup` キーワードでテストセットアップモジュールの名前を渡します：

```
@testsetup module TestIrrationals
    const PI = 3.14159
    const INV_PI = 0.31831
    area(radius) = PI * radius^2
    export PI, INV_PI, area
end
@testitem "Arithmetic" setup=[TestIrrationals] begin
    @test 1 / PI ≈ INV_PI atol=1e-6
end
@testitem "Geometry" setup=[TestIrrationals] begin
    @test area(1) ≈ PI
end
```

`@testitem` が不安定であることが知られている場合、つまり時々テストが通らない場合は、`retries` キーワードを渡すことで自動的に再試行するように設定できます。`@testitem` が再試行で通った場合、テストサマリーに通過として記録されます。

```
@testitem "Flaky test" retries=1 begin
    @test rand() < 1e-4
end
```

`@testitem` が特定の時間が経過した後に中止されるべき場合、例えばテストが時々ハングすることが知られている場合は、`timeout` キーワードを渡すことでタイムアウト（秒単位）を設定できます。`timeout` は現在、複数のワーカーでテストが実行されるときにのみ機能することに注意してください。

```
@testitem "Sometimes too slow" timeout=10 begin
    @test sleep(rand(1:100))
end
```

`@testitem` をスキップする必要がある場合は、`skip` キーワードを設定できます。`skip=true` を渡して無条件にテストアイテムをスキップするか、`skip` に `Bool` を返す式を渡してテストアイテムをスキップするかどうかを決定します。

```
@testitem "Skip on old Julia" skip=(VERSION < v"1.9") begin
    v = [1]
    @test 0 == @allocations sum(v)
end
```

`skip` 式は、テストアイテムと同様に独自のモジュールで実行されます。テストアイテムがスキップされると、`@testitem` 内のコードは実行されません。

`@testitem` が最初のテスト失敗で実行を停止する必要がある場合は、`failfast` キーワードを設定できます。

```
@testitem "stop early" failfast=true begin
    @test false
    @test true
    @test error("oops")
end
```
