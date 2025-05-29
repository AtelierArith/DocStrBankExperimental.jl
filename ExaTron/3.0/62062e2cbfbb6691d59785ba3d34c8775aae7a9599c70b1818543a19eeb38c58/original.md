Subroutine dtrqsol

This subroutine computes the largest (non-negative) solution of the quadratic trust region equation

||x + sigma*p|| = delta.

The code is only guaranteed to produce a non-negative solution if ||x|| <= delta, and p != 0. If the trust region equation has no solution, sigma = 0.

MINPACK-2 Project. March 1999. Argonne National Laboratory. Chih-Jen Lin and Jorge J. More'.
