---
title: Alice Gao Lecture Notes | Self-Study
date: January 20, 2023
---

# Alice Gao Lecture Notes [^1]

## MDP

- Revenue function $R(s,a,s')$
  - Here Revenue function might not depend on all of the parameters.

## Rewards

Assume $R(s)$: the reward of entering state $s$.

- Total Reward
  - Sum of Rewards at each time step.
  - If sum is infinite can't compare policies. 
- Average Reward
  - Divide *total reward* by the number of time steps $n$, such that $\lim_{n \rightarrow \infty}$.
  - For finite total reward, this'll always be zero.
- Discounted Reward
  - Discount factor $0\leq \gamma < 1$
  - Discount helps us set a preference over our rewards, in past and in future per se.

## Expected Utility of a Policy

$R(s)$ same as assumed before.

$V^\pi (s)$: Expected utility of **entering** state $s$, following policy $\pi$.

\begin{equation}
\label{eq:q}
Q^*(s,a) = \sum_{s'} P(s'|s,a) V^*(s')
\end{equation}

$Q$ is when we are already **in** a state and take an action. Essentially, it tells us the expected utility of **leaving** this state (by taking action $a$).

$\pi^*(s) = arg\max_{a} Q^*(s,a)$ 

### Relationship between $V$ and $Q$

\begin{equation}
\label{eq:vq}
V^*(s) = R(s) + \gamma \max_a Q^*(s,a)
\end{equation}

From \eqref{eq:q} and \eqref{eq:vq} we get the Bellman equation:

\begin{equation}
\label{eq:bellman}
V^*(s) = R(s) + \gamma \max_a \sum_{s'} P(s'|s,a) V^*(s')
\end{equation}

Goal states usually have a value already assigned to them. Also, unreachable states have a value as well (zero, mostly). For non-goal states, we'll have to solve the Bellman equation to get the optimal value function.

## Computing Bellman Equations Efficiently

We can't compute them efficiently in-general since $\max$ function is non-linear. So this is a non-linear problem.

Instead, we use an approximation approach, *Value Iteration* Approach.

### Value Iteration Algorithm

$V_i(s)$: values for $i$-th iteration

1. Start with arbitrary initial values $V_0(s)$
1. At the $i$-th iteration, compute $V_{i+1}(s)$ (sort of like gradient-descent update rule). Old values are plugged in to get the new values for next iteration.
1. Terminate when $\max_s |V_i(s) - V_{i+1}(s)|$ is small enough

If the updates are applied infinitely often, this algorithm is guaranteed to converge to optimal values.






[^1]: Reference: [Lec18](https://youtube.com/playlist?list=PLdBx38JxhMNvMw_C3KbeUOI_hCNPyVcyc) and [Lec19](https://youtube.com/playlist?list=PLdBx38JxhMNvwADKfTUI5uy3pmcPeLG2T)
