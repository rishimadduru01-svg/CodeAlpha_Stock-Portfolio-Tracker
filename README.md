# CodeAlpha_Stock-Portfolio-Tracker
# Stock Portfolio Tracker

# Hardcoded stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 140,
    "MSFT": 330,
    "AMZN": 150
}
total_investment = 0
try:
    n = int(input("Enter the number of stocks: "))
    for i in range(n):
        stock_name = input(f"\nEnter stock name {i+1}: ").upper()
        if stock_name in stock_prices:
            quantity = int(input("Enter quantity: "))
            investment = stock_prices[stock_name] * quantity
            total_investment += investment
            print(f"Investment in {stock_name}: ${investment}")
        else:
            print("Stock not found in price list.")
    print("\nTotal Investment Value: $", total_investment)
    save = input("\nDo you want to save the result? (yes/no): ").strip().lower()
    if save == "yes":
        try:
            with open("my_portfolio.txt", "w") as file:
                file.write(f"Total Investment Value: ${total_investment}\n")
            print("Result saved successfully in my_portfolio.txt")
        except Exception:
            print("File saving is not permitted on this platform.")
            print("Total Investment Value: $", total_investment)

except ValueError:
    print("Please enter valid numeric values.")
except Exception as e:
    print("An error occurred:", e)
