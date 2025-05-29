```
score = lecture_batched!(
    p::GenerativeFunction, p_args::Tuple,
    q::GenerativeFunction, get_q_args::Function)
```

Simulate a batch of traces of p representing training samples, and use them to update the gradients of the trainable parameters of q.

Like `lecture!` but q is batched, and must make random choices for training sample i under hierarchical address namespace i::Int (e.g. i => :z). get*q*args maps a vector of traces of p to an argument tuple of q.
