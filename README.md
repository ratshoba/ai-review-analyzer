# AI-Powered Customer Feedback Analyzer

## Business Question
Can an LLM automatically read and categorize customer reviews at scale, replacing the manual work of reading through thousands of reviews individually?

## Dataset
Women's E-Commerce Clothing Reviews (Kaggle) — licensed CC0: Public Domain, free to use and share with no restrictions.

## Tools Used
Python, Google Gemini API, pandas, matplotlib

## Approach
1. Loaded real customer review data from a Women's E-Commerce Clothing dataset
2. Designed a structured prompt asking Gemini to classify each review's sentiment and extract its main theme
3. Ran this analysis across a sample of reviews via the Gemini API
4. Aggregated the AI-generated labels to find patterns across the sample

## Key Finding
Out of a sample of real customer reviews, sentiment broke down as mostly Positive, with some Mixed and Negative. Notably, sizing and fit issues appeared as the dominant theme in half the reviews, regardless of overall sentiment (including several "Positive" reviews) — suggesting this is a business-wide pattern worth addressing through better size guides or fit descriptions, rather than a problem isolated to any single product.

## Business Implication
This approach can replace manual review reading at scale: instead of a team skimming thousands of reviews, an LLM processes them automatically and surfaces recurring themes, freeing up human attention for the patterns that actually matter.

## Challenges Faced
This project involved genuine real-world engineering problems beyond just writing prompts:
- **Deprecated SDK**: Google's original `google-generativeai` library was deprecated mid-project; migrated to the new `google-genai` package and updated the API syntax accordingly
- **Environment/compilation failure**: A dependency (`cryptography`) failed to compile in an older Python 3.9 environment; resolved by creating a fresh Python 3.11 environment and installing pre-built binary packages instead of building from source
- **Model versioning**: Model names referenced in tutorials became outdated within the same session; learned to query the API directly for currently available models rather than relying on hardcoded names, and to prefer "latest" aliases where available
- **Free-tier rate limits**: Hit daily request quotas (as low as 20 requests/day on some models) while testing; adapted by using a lighter-weight model, batching in smaller groups, and adding deliberate pacing between API calls

## Files
- `ai_review_analyzer.ipynb` — full notebook with code, AI prompts, results, and detailed write-up
- `Womens Clothing E-Commerce Reviews.csv` — dataset used for this analysis (CC0 licensed)
