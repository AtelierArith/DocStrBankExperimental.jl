```
marty(Wager, GamesPlayed; GameWinProb = 0.5, CashInHand = Wager)
```

*In probability theory, a martingale is a sequence of random variables (i.e., a stochastic process) for which, at a particular time, the conditional expectation of the next value in the sequence, given all prior values, is equal to the present value.* (Wikipedia)

The marty function is designed to simulate a Martigale such as that everytime a wager is lost, the next bet doubles the wagered amount to negate the previous loss. The resulting vector is the balance of cash the gambler has in hand at any given point in the Martingale process.

*GameWinProb* is the estimated probability of winning. *CashInHand* is the starting balance for the martigale. At times, this parameter can make a difference in whether your survive the process or go home broke.
