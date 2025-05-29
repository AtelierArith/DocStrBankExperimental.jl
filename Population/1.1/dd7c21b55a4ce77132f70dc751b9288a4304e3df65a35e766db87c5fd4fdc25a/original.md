Fixed Duration Age-Dependent Development Process

This age-dependent development process employs a step function, with discontunity at `devmn`, as the cumulative density function.

`AgeFixed()` returns a struct with fields:     - `pars`    takes a NamedTuple argument with `devmn` and `devsd` which computes `k`, `theta`, and `stay` (returned as a tuple in that order)     - `eval`    takes arguments `i`, `k`, and `theta` and returns the cumulative density function evaluated at `i`     - `func`    takes arguments `heval`, `d`, `q`, `k`, `theta`, and `qkey` and returns the hazard     - `check`   takes a Number argument and checks if process indicator breached completion threshold (by default 1.0)     - `stepper` takes a StepperTypes argument (e.g. `AccStepper`, `AgeStepper`, or `CustomStepper`).

The struct `AgeFixed` inherits from the abstract type `AgeHaz` (which itself has supertype `HazTypes`).
