//Author: Yermakov Ilya

How to Run in Visual Studio
1.	Open the .sln or .csproj file.
2.	In Solution Explorer, right-click the project and choose Set as Startup Project.
3.	Press Ctrl + F5 to run the app.
4.	
Questions & Answers
1. Which parts handle input and output?
Only the Main method handles I/O. It reads user input with Console.ReadLine() and prints text using Console.Write and Console.WriteLine. The calculation functions never interact with the console.

2. Which functions only calculate the price?
These are pure calculation functions with no console access:
CalculateItemPrice: adds a fee based on the number of items. 
CalculateDeliveryType: applies discounts or extra charges for the delivery type. 
zoneRule & expressRule: lambdas that add fees for zones outside the city and express delivery. 
ApplyRule: a higher-order function that runs any given rule on the price. 

3. How is Func<...> used to apply pricing rules?
Func<decimal, decimal> represents a rule that takes a price and returns a new price: 
It turns rules into variables (like zoneRule) so they can be passed around easily. 
It wraps methods with multiple parameters into a single-parameter function (e.g., p => CalculateItemPrice(p, itemCount)).
It lets us pass each rule directly into ApplyRule step by step. 

4. Why is TryParse useful?
TryParse checks and converts user text safely without crashing the program if the input is wrong. It returns true on success and false on failure, making it easy to show a friendly error message and stop the program safely with an early return
