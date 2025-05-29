The convex (narrow) Catoni loss function. See: "Catoni (2012) - Challenging the empirical mean and empirical variance: A deviation study"

ψ(r) = (abs(r) <= 1) ? -sign(r) * log(1 - abs(r) + r^2/2) : sign(r) * log(2)
