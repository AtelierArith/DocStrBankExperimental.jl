The 3-parameter non-convex bounded Hampel's loss function. ψ(r) = (abs(r) <= 1) ? r : (        (abs(r) <= l.ν1) ? sign(r) : (        (abs(r) <= l.ν2) ? (l.ν2 - abs(r)) / (l.ν2 - l.ν1) * sign(r) : 0))
