```
update = ParamUpdate(conf, param_lists...)
```

Return an update configured by `conf` that applies to set of parameters defined by `param_lists`.

Each element in `param_lists` value is is pair of a generative function and a vector of its parameter references.

**Example**. To construct an update that applies a gradient descent update to the parameters `:a` and `:b` of generative function `foo` and the parameter `:theta` of generative function `:bar`:

```julia
update = ParamUpdate(GradientDescent(0.001, 100), foo => [:a, :b], bar => [:theta])
```

---

Syntactic sugar for the constructor form above.

```
update = ParamUpdate(conf, gen_fn::GenerativeFunction)
```

Return an update configured by `conf` that applies to all trainable parameters owned by the given generative function.

Note that trainable parameters not owned by the given generative function will not be updated, even if they are used during execution of the function.

**Example**. If generative function `foo` has parameters `:a` and `:b`, to construct an update that applies a gradient descent update to the parameters `:a` and `:b`:

```julia
update = ParamUpdate(GradientDescent(0.001, 100), foo)
```
