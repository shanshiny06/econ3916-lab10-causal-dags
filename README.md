# econ3916-lab10-causal-dags
# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective
I set out to show that the same correlation can come from very different causal structures, and that adding a control variable can either fix a biased estimate or create one, depending on where that variable sits in the causal graph.

## Methodology
- I simulated three worlds (true causation, pure confounding and pure selection) built so that the correlation between treatment and outcome comes out near 0.65 in each, even though the true effects are 2.0, 0.0 and 0.0.
- I drew a confounder, a collider and a mediator as directed graphs with networkx so the causal paths in each structure were easy to see.
- I compared regressions with and without controls to show that controlling for a confounder recovers the true effect, while controlling for a collider creates a large, highly significant association between two variables that are independent.
- I built an M-bias structure in which a control measured before treatment still biases the estimate, to show that "pre-treatment" does not automatically mean "safe to control for."
- I wrote a small function, `coef_on_d()`, that returns the coefficient on the treatment for any list of controls. I used it to show that also controlling for one of the hidden causes (u1) closes the biasing path again.
- I reproduced the LaLonde (1986) contrast by comparing the randomised experiment against a comparison group drawn from the CPS, then measured how much of the gap covariate adjustment closes.

## Key Findings
- **Same correlation, different causes:** the three simulated worlds gave correlations of [YOUR VALUE], [YOUR VALUE] and [YOUR VALUE], even though only the first has a real effect. The correlation alone could not tell them apart.
- **Collider bias:** controlling for the collider gave a coefficient of [YOUR VALUE] where the truth is 0. Adding the wrong control created an effect out of nothing.
- **M-bias:** controlling for the pre-treatment variable gave [YOUR VALUE]. Once I also controlled for u1, the estimate moved to [YOUR VALUE], which shows that the bias came from the path the first control opened.
- **LaLonde:** the experimental estimate was $[YOUR VALUE], the naive CPS comparison gave $[YOUR VALUE], and adding controls gave $[YOUR VALUE]. Covariate adjustment closed [YOUR VALUE]% of the gap, so observed controls helped but did not fully replace randomisation.
