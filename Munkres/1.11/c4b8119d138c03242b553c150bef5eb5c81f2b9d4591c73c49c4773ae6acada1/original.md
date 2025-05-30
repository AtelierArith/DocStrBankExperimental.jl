Munkres (Hungarian) Algorithm for optimal assignment, i.e.  given an NxM cost matrix for assigning N workers to M jobs, what is the optimal allocation of tasks to workers such that one one task is assigned to one worker.

Input

  * cost_matrix - an NxM real valued matrix of the cost of assigning job m to worker N

Output

  * p - A vector of length N of assignments, where j = p[i] assigns job j to worker i.
