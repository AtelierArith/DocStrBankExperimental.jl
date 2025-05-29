```
maximize_logp(data, model, parameters = parameters(model);
              fixed = (;)
              coupled = [],
              lambda_l2 = 0.,
              hessian_ad = AutoForwardDiff(),
              gradient_ad = AutoForwardDiff(),
              evaluate_training = false,
              evaluate_test_data = nothing,
              evaluation_trigger = EventTrigger(),
              evaluation_options = (;),
              optimizer_options = (;),
              optimizer = default_optimizer(model, parameters; fixed, optimizer_options...),
              callbacks = [],
              verbosity = 1, print_interval = 3,
              return_g! = false,
              kw...
              )
```
