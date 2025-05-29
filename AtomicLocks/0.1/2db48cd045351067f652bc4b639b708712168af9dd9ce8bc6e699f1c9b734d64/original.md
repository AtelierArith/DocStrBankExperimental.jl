```
AtomicFIFOLock
```

An atomic lock that operates on a first-in, first-out (FIFO) basis. This ensures that requests to acquire the lock are handled in the order they are made, providing fairness in lock acquisition.

```
AtomicFIFOLock(wait=100)
```

Constructs an `AtomicFIFOLock`, which behaves similarly to a `SpinLock` or `AtomicLock`, but enforces a first-in, first-out (FIFO) order for acquiring the lock. This ensures that the lock is granted in the order in which it was requested, preventing the possibility of starvation that can occur with traditional spinlocks.

# Arguments

  * `wait`: Optional parameter that specifies the delay between attempts to acquire the lock. Defaults to 100 if not provided.

# Example

```julia fifo_lock = AtomicFIFOLock(200)  # Creates a FIFO lock with a custom wait time
