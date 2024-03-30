# Calculator_Project
import inquirer from "inquirer";

interface Input {
    value1: number;
    value2: number;
    operation: string;
}

async function main() {
    const input: Input = await inquirer.prompt([
        {
            type: "number",
            name: "value1",
            message: "Enter the first number:"
        },
        {
            type: "number",
            name: "value2",
            message: "Enter the second number:"
        },
        {
            type: "list",
            name: "operation",
            message: "Select operation:",
            choices: [
                "+",
                "-",
                "*",
                "/"
            ]
        }
    ]);

    const { value1, value2, operation } = input;

    if (value1 !== undefined && value2 !== undefined && operation) {
        let result: number = 0; 
        if (operation === "+") {
            result = value1 + value2;
        } else if (operation === "-") {
            result = value1 - value2;
        } else if (operation === "*") {
            result = value1 * value2;
        } else if (operation === "/") {
            result = value1 / value2;
        } else {
            console.log("Invalid operation selected.");
            return;
        }
        console.log("Your result is:", result);
    } else {
        console.log("Please enter valid numbers and operation.");
    }
}

main();
