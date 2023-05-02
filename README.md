#include <stdio.h>
#include <string.h>

int process_string(char *str);

int main() {
    char str[100];
    printf("Enter a string with two words: ");
    fgets(str, sizeof(str), stdin);
    // Removing the newline character at the end
    str[strcspn(str, "\n")] = '\0';

    int result = process_string(str);

    printf("\nThe length of the string is %d\n", strlen(str));
    printf("The function returned %d\n", result);

    return 0;
}

int process_string(char *str) {
    char word1[50], word2[50];

    // Splitting the string into two words
    sscanf(str, "%s %s", word1, word2);

    // Converting the first word to upper case first letter and lower case for the rest
    word1[0] = toupper(word1[0]);
    for (int i = 1; i < strlen(word1); i++) {
        word1[i] = tolower(word1[i]);
    }

    // Converting the second word to upper case
    for (int i = 0; i < strlen(word2); i++) {
        word2[i] = toupper(word2[i]);
    }

    // Printing the revised string and its length
    printf("%s %s\n", word1, word2);
    printf("%ld\n", strlen(str));

    // Returning the length of the string or its size depending on its length
    if (strlen(str) < 20) {
        return strlen(str);
    } else {
        return sizeof(str);
    }
}
