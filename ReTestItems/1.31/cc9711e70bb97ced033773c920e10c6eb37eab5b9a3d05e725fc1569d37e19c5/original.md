```
@testitem "name" [tags=[] setup=[] retries=0 skip=false default_imports=true] begin
    # code that will be run as tests
end
```

A single, independently runnable group of tests.

A test item is a standalone block of tests, and cannot access names from the surrounding scope. Multiple test items may run in parallel, executing on distributed processes.

A `@testitem` can contain a single test:

```
@tesitem "Arithmetic" begin
    @test 1 + 1 == 2
end
```

Or it can contain many tests, which can be arranged in `@testsets`:

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

A `@testitem` is wrapped into a module when run, so must import any additional packages:

```
@testitem "Arithmetic" begin
    using LinearAlgebra
    @testset "multiplication" begin
        @test dot(1, 2) == 2
    end
end
```

The test item's code is run as top-level code in a new module, so it can include imports, define new structs or helper functions, and declare tests and testsets.

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

By default, `Test` and the package being tested will be loaded into the `@testitem`. This can be disabled by passing `default_imports=false`.

A `@testitem` can use test-specific setup code declared with `@testsetup`, by passing the name of the test setup module with the `setup` keyword:

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

If a `@testitem` is known to be flaky, i.e. contains tests that sometimes don't pass, then you can set it to automatically retry by passing the `retries` keyword. If a `@testitem` passes on retry, then it will be recorded as passing in the test summary.

```
@testitem "Flaky test" retries=1 begin
    @test rand() < 1e-4
end
```

If a `@testitem` should be aborted after a certain period of time, e.g. the test is known to occassionally hang, then you can set a timeout (in seconds) by passing the `timeout` keyword. Note that `timeout` currently only works when tests are run with multiple workers.

```
@testitem "Sometimes too slow" timeout=10 begin
    @test sleep(rand(1:100))
end
```

If a `@testitem` needs to be skipped, then you can set the `skip` keyword. Either pass `skip=true` to unconditionally skip the test item, or pass `skip` an expression that returns a `Bool` to determine if the testitem should be skipped.

```
@testitem "Skip on old Julia" skip=(VERSION < v"1.9") begin
    v = [1]
    @test 0 == @allocations sum(v)
end
```

The `skip` expression is run in its own module, just like a test-item. No code inside a `@testitem` is run when a test-item is skipped.

If a `@testitem` should stop running on the first test failure, then you can set the `failfast` keyword.

```
@testitem "stop early" failfast=true begin
    @test false
    @test true
    @test error("oops")
end
```
