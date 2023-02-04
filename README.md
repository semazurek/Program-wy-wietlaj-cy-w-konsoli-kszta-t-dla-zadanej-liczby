# Program wyświetlający w konsoli kształt dla zadanej liczby
Programowanie C# "Napisz program wyświetlający na konsoli następujący kształt dla zadanej liczby n. </br>
Tablica dwuwymiarowa/macierz.
</br></br>
![324695587_1254267091821534_8157371220208702656_n](https://user-images.githubusercontent.com/85984736/216754204-703f191a-f1d3-46bf-b3f0-91608a4741d5.png)
</br></br>
```csharp
using System;
using System.Xml.Serialization;

Start:
Console.Write("Podaj N: ");
int k = Convert.ToInt32(Console.ReadLine());

//temp k value;

int[,] array2D = { //2x1
    {1},
    {1}
};

int[,] arrayTEMP = { //2x1
    {1},
    {1}
};


// show array2D + info
void show()
{
    for (int i = 0; i < array2D.GetLength(0); i++)
    {
        for (int j = 0; j < array2D.GetLength(1); j++)
        {
            Console.Write(array2D[i, j] + " ");
        }
        Console.WriteLine();
    }

}

//func change size to n (n=2 -> [3,2])
void resize(int n)
{
    if (n >= 1)
    {
        array2D = new int[n + 1, n];
    }
}

void resizeTEMP(int n)
{
    if (n >= 1)
    {
        arrayTEMP = new int[n + 1, n];
    }
}

void copy_and_fill(int n)
{
    //even numb 2,4,6,8... filling left n number borders
    if (n % 2 == 0)
    {
        //copy from arrayTEMP to array2D EVEN NUMB
        for (int x = 0; x < arrayTEMP.GetLength(0); x++)
        {
            for (int y = 0; y < arrayTEMP.GetLength(1); y++)
            {
                array2D[x, y + 1] = arrayTEMP[x, y];
            }
        }

        //filling number
        for (int i = 0; i < array2D.GetLength(0); i++)
        {
            for (int j = 0; j < array2D.GetLength(1); j++)
            {
                if (j == 0) array2D[i, j] = n;
                if (i == array2D.GetLength(1)) array2D[i, j] = n;
            }
        }
    }
    //odd numb 1,3,5,7,9... filling right side n number borders
    else //(n % 2 != 0)
    {
        //copy from arrayTEMP to array2D ODD NUMB
        for (int x = 0; x < arrayTEMP.GetLength(0); x++)
        {
            for (int y = 0; y < arrayTEMP.GetLength(1); y++)
            {
                array2D[x + 1, y] = arrayTEMP[x, y];
            }
        }

        //filling number
        for (int i = 0; i < array2D.GetLength(0); i++)
        {
            for (int j = 0; j < array2D.GetLength(1); j++)
            {
                if (j == n - 1) array2D[i, j] = n;
                if (i == 0) array2D[i, j] = n;
            }
        }
    }
}

void backupTEMP()
{
    for (int x = 0; x < arrayTEMP.GetLength(0); x++)
    {
        for (int y = 0; y < arrayTEMP.GetLength(1); y++)
        {
            arrayTEMP[x, y] = array2D[x, y];
        }
    }
}

for(int licz=2;licz<k+1;licz++)
{
    resize(licz);
    copy_and_fill(licz);
    resizeTEMP(licz);
    backupTEMP();

}
show();

goto Start;


```
