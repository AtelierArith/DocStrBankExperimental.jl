```
ControlledPlant{ST, CT, XT, DT, PT, CPRT, CPST} <: AbstractControlProblem
```

Struct representing a closed-loop controlled system.

### Fields

  * `ivp`            – initial-value problem
  * `controller`     – controller
  * `vars`           – dictionary storing state variables, input variables and                     control variables
  * `period`         – control period
  * `postprocessing` – postprocessing of the controller output
  * `preprocessing`  – preprocessing of the controller input

### Parameters

  * `ST`:  type of system
  * `CT`:  type of controller
  * `XT`:  type of initial condition
  * `DT`:  type of variables
  * `PT`:  type of period
  * `CPRT`: type of control preprocessing
  * `CPST`: type of control postprocessing

### Notes

While typically the `controller` is a neural network, this struct does not prescribe the type.
