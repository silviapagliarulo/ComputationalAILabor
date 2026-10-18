# AI Adoption, Labor Market Polarization and Income Inequality

**Agent-Based Model with Imitation Dynamics**

Lucia D'Amore · Nora Donelli · Silvia Pagliarulo · Sofia Perondi
A.Y. 2025–2026 — Sant'Anna School of Advanced Studies & University of Pisa
"Computational Economics" — Proff. G. Fagiolo, A. Roventini, A. Vandin

## Overview

An Agent-Based Model (ABM) of AI adoption by firms and its distributional
consequences on the labour market, calibrated to recent evidence on
early-career employment losses in AI-exposed occupations (Brynjolfsson et
al., 2025a). The model extends a Boltzmann wealth framework with:

- a bipartite firm-worker labour network;
- stochastic Poisson AI adoption with Axelrod/Bass imitation dynamics;
- seniority-asymmetric displacement rules;
- a savings-constrained retraining pathway that generates a poverty trap.

## Key Findings

- Inequality is **transient but non-self-correcting**: the Gini coefficient
  peaks mid-horizon and only partially recedes.
- A small terminal wage gap (~4%) compounds into a large savings gap
  (Polarization Index ≈ 1.21).
- The binding constraint on recovery is **liquidity at the moment of
  displacement**, not worker preferences.
- Low patience decay (δ) and a high retraining buffer (B_months) compound to
  produce the most adverse regime.

## Model Architecture

| Component   | Description                                              |
|-------------|----------------------------------------------------------|
| Baseline    | Closed economy, equal endowments, Gini = 0, Polarization = 1 |
| Extension 1 | Stochastic adoption, asymmetric firing, constrained retraining |
| Extension 2 | Mean-field imitation (Bass diffusion), λ_i(t) = λ0 + γ·F(t) |

## Calibration

Parameters calibrated via Simulated Method of Moments (SMM) targeting the
facts of Brynjolfsson et al. (2025a):

- 16% relative decline in early-career employment in AI-exposed occupations;
- no AI-driven decline for experienced workers;
- wage-gap-to-employment-gap ratio ≈ 0.15.

## Statistical Validation

Monte Carlo replications (N = 50) sized via Statistical Model Checking (SMC):

- Polarization Index: relative half-width ≤ 5%;
- Gini coefficient: absolute half-width ≤ 0.01.

## Directory Structure

    .
    ├── model/          # ABM implementation (Mesa / Python)
    ├── calibration/    # SMM grid-search scripts
    ├── smc/            # Statistical Model Checking driver
    ├── simulations/    # Monte-Carlo experiment runner
    ├── figures/        # Generated plots
    ├── data/           # Calibration targets
    └── paper/          # LaTeX source

## Reproduction

    pip install mesa numpy scipy pandas matplotlib
    python calibration/run_smm.py
    python simulations/run_mc.py --n-reps 50 --horizon 150
    python simulations/plot_results.py

## References

- Brynjolfsson, Chandar & Chen (2025a). Canaries in the coal mine? Stanford Digital Economy Lab.
- Bass (1969). A new product growth model. Management Science, 15(5).
- Dragulescu & Yakovenko (2002). Statistical mechanics of money. arXiv:cond-mat/0211175.
- Dynan, Skinner & Zeldes (2004). Do the rich save more? JPE, 112(2).
- Kline et al. (2019). Who profits from patents? QJE, 134(3).
- Vandin (2024). Statistical model checking of Python ABMs. Springer.
