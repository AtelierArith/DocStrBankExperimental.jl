A non-interactive pendulum environment.

Accepts only `nothing` actions, which result in the system being simulated for one time step. Sets `env.done` to `true` once `maximum_time` is reached. Resets to a random position and momentum. Always returns zero rewards.

Useful for debugging and development purposes, particularly in model-based reinforcement learning.
