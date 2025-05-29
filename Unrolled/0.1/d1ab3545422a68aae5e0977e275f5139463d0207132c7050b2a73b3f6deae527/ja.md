`@fixed_range 3:10` は標準の範囲 `3:10` のように動作しますが、型システム内に格納されるため、`some_tuple[@fixed_range 3:10]` は型が安定します。また、`some_tuple[@fixed_range 3:end-5]` もサポートしています。
