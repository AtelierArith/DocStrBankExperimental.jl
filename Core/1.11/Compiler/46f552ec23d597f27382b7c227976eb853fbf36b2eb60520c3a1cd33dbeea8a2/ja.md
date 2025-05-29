```
opt_params::OptimizationParams
```

オプティマイザの動作を制御するパラメータ。

---

  * `opt_params.inlining::Bool = inlining_enabled()` インライン化が有効かどうかを制御します。

---

  * `opt_params.inline_cost_threshold::Int = 100` インライン化する価値がないCPUサイクルの数を指定します。

---

  * `opt_params.inline_nonleaf_penalty::Int = 1000` 動的ディスパッチのペナルティコストを指定します。

---

  * `opt_params.inline_tupleret_bonus::Int = 250` 非具体的なタプル戻り型を持つメソッド特殊化に対する追加のインライン化意欲を指定します（分割を期待して）。インライン化の決定を行う際に、`opt_params.inline_tupleret_bonus`が`opt_params.inline_cost_threshold`に加算されます。

---

  * `opt_params.inline_error_path_cost::Int = 20` `throw`が発生することが知られているブロック内での最適化されていない動的呼び出しのペナルティコストを指定します。詳細は[`(inf_params::InferenceParams).unoptimize_throw_blocks`](@ref InferenceParams)を参照してください。

---

  * `opt_params.max_tuple_splat::Int = 32` `Core._apply_iterate`をインライン化しようとする際に、タプルがこの数以上の要素を含む場合は最適化を中止します。

---

  * `opt_params.compilesig_invokes::Bool = true` `true`の場合、`@nospecialize`注釈に基づいて`:invoke`式を生成する際に、どの`MethodInstance`を呼び出すかを変更するためにインライナーにライセンスを与え、過剰な特殊化を避けます。

---

  * `opt_params.assume_fatal_throw::Bool = false` `true`の場合、オプティマイザは任意の`throw`が致命的であると仮定し、したがって`throw`の後の状態は外部から観察できないと仮定します。特に、これはオプティマイザに、特定のコードパス内で観察されないことが証明された副作用を投げる呼び出しの前後で移動するライセンスを与えます。デフォルトは`false`です。

---

  * `opt_params.preserve_local_sources::Bool = false` `true`の場合、インライナーは`CallInfo`オブジェクトに保持されているローカルキャッシュされたソースを変更することが制限され、常にそれらを呼び出し元コンテキストにインライン化する前にコピーを作成します。デフォルトは`false`です。

---
