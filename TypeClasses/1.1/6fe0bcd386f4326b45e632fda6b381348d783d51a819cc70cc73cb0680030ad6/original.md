ap(f::F1, a::F2) -> F3

Apply function in container `F1` to element in container `F2`, returning results in the same container `F3`. The default implementation uses `flatmap` and `map`, so that in general only those two need to be defined.
