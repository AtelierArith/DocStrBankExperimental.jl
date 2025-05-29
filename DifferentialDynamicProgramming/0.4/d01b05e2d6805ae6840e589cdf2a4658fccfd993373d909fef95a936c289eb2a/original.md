iLQG - solve the deterministic finite-horizon optimal control problem.

minimize sum_i cost(x[:,i],u[:,i]) + cost(x[:,end]) s.t.  x[:,i+1] = f(x[:,i],u[:,i])

# Inputs

`f, costfun, df`

1. step:

`xnew = f(x,u,i)` is called during the forward pass. Here the state x and control u are vectors: size(x)==(n,), size(u)==(m,). The time index `i` is a scalar.

2. cost:

`cost = costfun(x,u)` is called in the forward pass to compute the cost per time-step along the trajectory `x,u`.

3. derivatives:

`fx,fu,fxx,fxu,fuu,cx,cu,cxx,cxu,cuu = df(x,u)` computes the derivatives along a trajectory. In this case size(x)==(n, N) where N is the trajectory length. size(u)==(m, N). The time indexes are I=(1:N). Dimensions match the variable names e.g. size(fxu)==(n, n, m, N) If cost function or system is time invariant, the dimension of the corresponding derivatives can be reduced by dropping the time dimension

`x0` - The initial state from which to solve the control problem. Should be a column vector. If a pre-rolled trajectory is available then size(x0)==(n, N) can be provided and cost set accordingly.

`u0` - The initial control sequence. A matrix of size(u0)==(m, N) where m is the dimension of the control and N is the number of state transitions.

# Outputs

`x` - the optimal state trajectory found by the algorithm. size(x)==(n, N)

`u` - the optimal open-loop control sequence. size(u)==(m, N)

`traj_new` - A new `GaussianPolicy` object containing feedforward control trajectory and feedback-gains, these gains multiply the deviation of a simulated trajectory from the nominal trajectory x. See `?GaussianPolicy` for more help.

`Vx` - the gradient of the cost-to-go. size(Vx)==(n, N)

`Vxx` - the Hessian of the cost-to-go. size(Vxx)==(n, n N)

`cost` - the costs along the trajectory. size(cost)==(1, N) the cost-to-go is V = fliplr(cumsum(fliplr(cost)))

`trace` - a trace of various convergence-related values. One row for each iteration, the columns of trace are `[iter λ α g_norm Δcost z sum(cost) dλ]` see below for details.

# Keyword arguments

`lims`,           [],            control limits

`α`,              logspace(0,-3,11), backtracking coefficients

`tol_fun`,         1e-7,          reduction exit criterion

`tol_grad`,        1e-4,          gradient exit criterion

`max_iter`,        500,           maximum iterations

`λ`,         1,             initial value for λ

`dλ`,        1,             initial value for dλ

`λfactor`,   1.6,           λ scaling factor

`λmax`,      1e10,          λ maximum value

`λmin`,      1e-6,          below this value λ = 0

`regType`,        1,             regularization type 1: q*uu+λ*I 2: V*xx+λ*I

`reduce_ratio_min`,           0,             minimal accepted reduction ratio

`diff_fun`,         -,             user-defined diff for sub-space optimization

`plot`,           1,             0: no  k>0: every k iters k<0: every k iters, with derivs window

`verbosity`,      2,             0: no  1: final 2: iter 3: iter, detailed

`plot_fun`,         x->0,          user-defined graphics callback

`cost`,           [],            initial cost for pre-rolled trajectory

This code consists of a port and extension of a MATLAB library provided by the autors of `INPROCEEDINGS{author={Tassa, Y. and Mansard, N. and Todorov, E.}, booktitle={Robotics and Automation (ICRA), 2014 IEEE International Conference on}, title={Control-Limited Differential Dynamic Programming}, year={2014}, month={May}, doi={10.1109/ICRA.2014.6907001}}`
