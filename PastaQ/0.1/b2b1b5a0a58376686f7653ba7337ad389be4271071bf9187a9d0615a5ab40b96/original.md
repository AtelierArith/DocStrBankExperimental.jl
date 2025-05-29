```
tomography(train_data::AbstractMatrix, L::LPDO;
           optimizer::Optimizer,
           observer! = nothing,
           kwargs...)
```

Run quantum process tomography using a variational model $L$ to fit `train_data`. Depending on the type of `train_data`, run state or process tomography (see full tomography docs for the data format).

For quantum state tomography, optimize the average Kullbach-Leibler (KL) divergence for projective measurements in a set of bases:

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log P(x_k^{(b)})
$$

where the cost function is computed as

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log |\langle x_k|U_b|\psi(\theta)\rangle|^2
$$

for input MPS variational wavefunction, and

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log \langle x_k|U_b \rho(\theta) U_b^\dagger|x_k\rangle
$$

for input LPDO variational density operators. Here $U_b$ is the depth-1 unitary that rotates the variational state into the measurement basis $b$ for outcome $x^{(b)}$.

For quantum process tomography, optimize the  KL divergence for the process probability distribution

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log P(x_k^{(b)}|\xi)
$$

where $\xi$ is the input state to the channel. The cost function is computed as

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log |\langle x_k|U_b|\tilde\Phi(\theta)\rangle|^2
$$

for input MPO variational unitary operator (trated as a MPS $|\Phi\rangle$ after appropriate vectorization), and

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log \langle x|U_b \tilde\Lambda(\theta) U_b^\dagger|x\rangle
$$

for input LPDO variational Choi matrix. Here we refer to $\tilde\Phi$ and $\tilde\Lambda$ respectively as the projection of the unitary operator or Choi matrix into the input state $|\xi\rangle$ to the channel.

Keyword arguments:

  * `train_data`: pairs of preparation/ (basis/outcome): `("X+"=>"X"=>0, "Z-"=>"Y"=>1, "Y+"=>"Z"=>0, …)`.
  * `L`: variational model (MPO/LPDO).
  * `optimizer`: optimizer object for stochastic optimization (from `Optimisers.jl`).
  * `observer!`: if provided, keep track of training metrics (from `Observers.jl`).
  * `batch_size`: number of samples used for one gradient update.
  * `epochs`: number of training iterations.
  * `target`: target quantum state/process for distance measures (e.g. fidelity).
  * `test_data`: data for computing cross-validation.
  * `observer_step = 1`: how often the Observer is called to record measurements.
  * `outputlevel = 1`: amount of information printed on screen during training.
  * `outputpath`: if provided, save metrics on file.
  * `savestate`: if `true`, save the variational state on file.
  * `print_metrics = []`: print these metrics on screen during training.
  * `earlystop`: if `true`, use pre-defined early-stop function. A function can also be passed  as `earlystop`, in which case if the function (evaluated at each iteration) returns `true`,  the training is halted.
