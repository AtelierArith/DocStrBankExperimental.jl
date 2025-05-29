```
score = lecture!(
    p::GenerativeFunction, p_args::Tuple,
    q::GenerativeFunction, get_q_args::Function)
```

Simulate a trace of p representing a training example, and use to update the gradients of the trainable parameters of q.

Used for training q via maximum expected conditional likelihood. Random choices will be mapped from p to q based on their address. get*q*args maps a trace of p to an argument tuple of q. score is the conditional log likelihood (or an unbiased estimate of a lower bound on it, if not all of q's random choices are constrained, or if q uses non-addressable randomness).
