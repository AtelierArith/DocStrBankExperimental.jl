```
isinplace(f, inplace_param_number, fname = "f", iip_preferred = true;
          has_two_dispatches = true,
          outofplace_param_number = inplace_param_number - 1)
isinplace(f::AbstractSciMLFunction[, inplace_param_number])
```

関数が引数の数を期待される数と比較することによって、インプレースで動作するかどうかを確認します。`f`が`AbstractSciMLFunction`である場合、型パラメータは正しいと見なされ、使用されます。そうでない場合、`inplace_param_number`はメソッドテーブルに対してチェックされ、`inplace_param_number`はインプレースディスパッチの引数の数です。アウトオブプレースディスパッチは、デフォルトでインプレースバージョンより1つ少ない`outofplace_param_number`パラメータを持つと見なされます。これらのディスパッチのいずれも存在しない場合、エラーがスローされます。エラーがスローされた場合、`fname`はどの関数が不正なディスパッチを持っているかをユーザーに伝えるために使用されます。

`iip_preferred`は、`inplace_param_number=4`で、3引数と4引数の両方のメソッドが存在する場合、インプレースとして選択されることを意味します。`iip_dispatch`はこの決定を反転させます。

`has_two_dispatches = false`の場合、正しいディスパッチは1つだけであると見なされ、すなわち最適化関数のための`f(u,p)`であり、したがってoop形式のチェックは無効になり、2引数のシグネチャが一致することが保証されます。

# 参照

  * [`numargs`](@ref numargs)

```
