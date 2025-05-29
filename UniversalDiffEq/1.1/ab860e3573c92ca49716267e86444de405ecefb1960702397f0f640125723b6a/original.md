train!(UDE::UDE; kwargs...)

This function provides access to several training routines for UDE models. The user provides the UDE model object and can then choose between several loss functions and optimization algorithms using the keyword arguments. The training routine will update the UDE object with the trained parameters and return any other useful quantities estimated during the training procedure. The default optimizer trains the UDE model by minimizing the loss function using the ADAM gradient descent algorithm for `maxiter` steps of size `step_size`. Five loss functions are available using the `loss_function` argument: conditional likelihood, marginal likelihood, derivative matching, shooting, and multiple shooting. The `loss_options` and `optim_options` arguments are named tuples that can be used to pass parameters to the training routine.

# kwargs

  * `loss_function`: Determines the loss function used to train the model and defaults to "derivative matching" for efficiency.
  * `verbose`: If true, the value of the loss function will print between each step of the optimizer.
  * `regularization_weight`: Weight given to regularization in the loss function. Default is 0.
  * `optimizer`: Determines the optimization algorithm used to train the model and defaults to "ADAM" for gradient descent.
  * `loss_options`: Named tuple with keyword arguments to help construct the loss function.
  * `optim_options`: Named tuple with keyword arguments to pass to the optimization algorithm. For ADAM, these are `maxiter`, the number of iterations used to run the algorithm, and `step_size`, the size of each iteration.

# Loss Functions

Users can choose from one of five loss functions: conditional likelihood, marginal likelihood, derivative matching, shooting, and multiple shooting.

|          Loss Function | Discrete Model | Continuous Model |    Speed |
| ----------------------:| --------------:| ----------------:| --------:|
| Conditional likelihood |            Yes |              Yes | Moderate |
|    Marginal likelihood |            Yes |              Yes |     Slow |
|    Derivative matching |             No |              Yes |     Fast |
|               Shooting |             No |              Yes | Moderate |
|      Multiple shooting |             No |              Yes | Moderate |

## Conditional likelihood:

To use the conditional likelihood set the keyword argument `loss_function = "conditional likelihood"`.

This option trains the UDE model while accounting for imperfect observations and process uncertainty by maximizing the conditional likelihood of a state-space model where the UDE is used as the process model. The conditional likelihood is faster to compute, but can be less accurate than the marginal likelihood.

## Marginal likelihood:

To use the marginal likelihood set the keyword argument `loss_function = "marginal likelihood"`.

This option maximizes the marginal likelihood of a state-space model, which is approximated using an unscented Kalman filter. This option is slower than the conditional likelihood but should, in theory, increase the accuracy of the trained model (i.e., reduce bias).

### loss_options

  * `process_error`: An initial estimate of the level of process error. Default is 0.1.
  * `observation_error`: The level of observation error in the data set. There is no default, so it will throw an error if not provided.
  * `α`: Parameter for the Kalman filter algorithm. Default is 10^-3.
  * `β`: Parameter for the Kalman filter algorithm. Default is 2.
  * `κ`: Parameter for the Kalman filter algorithm. Default is 0.

## Derivative matching:

To use the derivative matching training routine set `loss_function = "derivative matching"`.

This function trains the UDE model in a two-step process. First, a smoothing function is fit to the data using a spline regression. Then, the UDE model is trained by comparing the derivatives of the smoothing functions to the derivatives predicted by the right-hand side of the UDE. This training routine is much faster than the alternatives, but may be less accurate.

### loss_options

  * `d`: The number of degrees of freedom in the curve fitting function. Defaults to 12.
  * `alg`: The algorithm used to fit the curve to the data set. See the DataInterpolations package for details. Defaults to generalized cross-validation `:gcv_svd`.
  * `remove_ends`: The number of data points to leave off of the end of the data set when training the UDE to reduce edge effects from the curve fitting process. Defaults to 0.

## Shooting:

To use the shooting training routine set `loss_function = "shooting"`.

This option calculates the loss by solving the ODE from the initial to the final data point and comparing the observed to the predicted trajectory with mean squared error (MSE). The initial data point is estimated as a free parameter to reduce the impacts of observation error.

## Multiple shooting:

To use the multiple shooting training routine set `loss_function = "multiple shooting"`.

This option calculates the loss by breaking the data into blocks of sequential observations. It then uses the UDE to forecast from the initial data point in each block to the first data point in the next block. The loss is defined as the MSE between the forecasts and the data points. The initial data point in each block is estimated as a free parameter to reduce the impacts of observation error.

### loss_options

  * `pred_length`: The number of data points in each block. The default is 10.

# Optimization Algorithms

The method used to minimize the loss function. Two options are available: ADAM and BFGS. ADAM is a first-order gradient descent algorithm, while BFGS is a quasi-Newton method that uses approximate second-order information.

The user can specify the maximum number of iterations `maxiter` for each algorithm using the `optim_options` keyword argument. For ADAM the `optim_options` can be used to specify the step size `step_size` and for BFGS you can specify the initial step norm `initial_step_norm`.
