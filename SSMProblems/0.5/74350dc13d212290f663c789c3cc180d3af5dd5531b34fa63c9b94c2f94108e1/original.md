A state space model.

A vanilla implementation of a state space model, composed of a latent dynamics and an observation process.

# Fields

  * `dyn::LD`: The latent dynamics of the state space model.
  * `obs::OP`: The observation process of the state space model.

# Parameters

  * `T`: The arithmetic type of the state space model, which the latent dynamics and       observation process should be consistent with.
  * `LD`: The type of the latent dynamics.
  * `OP`: The type of the observation process.
